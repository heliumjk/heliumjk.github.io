---
id: 23
title: 'Laravel Permissions &#8211; Working with Roles'
date: 2019-02-24T23:00:55-08:00
author: ed@normalllc.com
layout: post
guid: https://edanisko.com/?p=23
permalink: /laravel-permissions-working-with-roles/
xyz_smap:
  - "1"
categories:
  - Laravel
tags:
  - laravel nova spatie permissions gate seeder policy
---
{% include JB/setup %}
**Install the Package**

Laravel has a way of authorizing a user to act on an object. Please read the [docs](https://laravel.com/docs/master/authorization) if you like. You will start off writing Gates. Gates allow and deny access to actions. You can define Gate <!--more--> with closures. You can point the Gate to a Policy method which is defined somewhere else. Then you try to figure out where to put the gate. I didn’t get far because half -way through docs I noticed this guy:



<pre data-mode="php" data-theme="monokai" data-fontsize="14" data-lines="Infinity" class="wp-block-simple-code-block-ace">&lt;?php

//TODO: wth is isSuperAdmin()
//TODO: is $ability used for anything??

Gate::before(function ($user, $ability) {
    if ($user->isSuperAdmin()) {
        return true;
    }
});

// TL;DR = This is the hard way.
</pre>

I’ve installed Laravel more times than I’d like to admit. So I know that the prefab App\User class does not have the function isSuperAdmin(). Because this is what I want, I stopped reading. What I want is a simple way to authorize user actions against a given resource. Permissions or Roles, something like that.

<pre class="wp-block-code"><code>google: laravel permissions roles</code></pre>

First thing up is [spatie/laravel-permissions](https://github.com/spatie/laravel-permission). Of course there are others, but this is the one. Spatie is similiar to zizaco/entrust. I used entrust once on a project in 2017 and it worked ok. Unfortunately it looks like no one has updated since 2017. Unfortunately I didn’t pick spatie back then. So search around if you like or simply:

<pre class="wp-block-code"><code>composer require spatie/laravel-permission</code></pre>

#### Follow the Directions

Setting up laravel-permissions is about as hard as setting up a plugin gets. Here are the basic steps:

  * composer require
  * modify providers in config/app.php
  * publish the migration 
  * migrate your application

I read these docs a few times. Authorization structures can be quite complex. The effects of doing it wrong can lead to serious, even catastrophic business implications. Authentication lets a user in. Authorization will stop users from performing high level actions. Install the package and follow the directions and you will be able to do things like:

<pre data-mode="php" data-theme="monokai" data-fontsize="14" data-lines="Infinity" class="wp-block-simple-code-block-ace">&lt;?php

// TL;DR = This is the easy way.

Permission::create(['name' => 'force delete all users']);

$new_role = Role::create(['name' => 'superadmin']);
$new_role->givePermissionTo(Permission::all());

$user = User::find(1); //assuming this is you
$user->assignRole('superadmin');

//then later
if( $user->can('force delete all users') )
{
    User::truncate(); //or whatever
}
</pre>

#### Seeding Roles and Permissions

So now you can create Permissions and/or Roles and assign them to Objects. This is where the docs go silent. It turns out there are only a few actions that can be performed on an object and that&#8217;s nice. Therefore only a few permissions per object are needed to govern these actions. They are as follows:

  * viewAny
  * view
  * create
  * update
  * delete
  * forceDelete
  * restore
  * add
  * attach
  * detach
  * attachAny

This list is the basket of cruddy actions available in Laravel. I have combined Laravel Nova here as well. Consider the App\Comment object in a a blog. You wind up with a creating a set of permissions like this:

<pre data-mode="php" data-theme="monokai" data-fontsize="14" data-lines="Infinity" class="wp-block-simple-code-block-ace">&lt;?php
//creating permissions for App\Comment

Permission::create(['name' => 'view any comment']); // think of this as 'hide all the posts??''
Permission::create(['name' => 'view comment']);
Permission::create(['name' => 'create comment']);
Permission::create(['name' => 'update comment']);
Permission::create(['name' => 'delete comment']); // soft delete
Permission::create(['name' => 'force delete comment']); // destroy
Permission::create(['name' => 'restore comment']); // restore a soft delete
Permission::create(['name' => 'add comment']); // used with relationships 
Permission::create(['name' => 'attach comment']); // used with many to many relationships 
Permission::create(['name' => 'detach comment']); // inverse of attach 
Permission::create(['name' => 'attach any comment']); // disallow a user from attaching this model to anything

</pre>

That&#8217;s just for App\Comment. Do the same for User, Post and Tags there are quite a few permissions piling up. Lots of typeing. Now you have to attach them to Roles. Admin, Moderator, User, Guest&#8230; nightmare. I have an app with 26 objects and 5 roles. That&#8217;s 260 permissions and a possible 1300 grants. A colleague told me years ago, &#8220;if you copy and pasted it more than twice, you&#8217;re doing it wrong&#8221;. So this this problem qualifies some kind of configuration management.

I turned to the Lavavel database seeder and came up with this:

<pre class="wp-block-code"><code>php artisan make:seeder RoleSeeder</code></pre>

<pre data-mode="php" data-theme="monokai" data-fontsize="14" data-lines="Infinity" class="wp-block-simple-code-block-ace">&lt;?php

use App\User;
use Illuminate\Database\Seeder;
use Illuminate\Support\Facades\DB;
use Spatie\Permission\Models\Role;
use Spatie\Permission\Models\Permission;

class RoleSeeder extends Seeder
{
    /**
     * Seed roles and permissions using spatie/permissions.
     *
     * @return void
     */
    public function run()
    {

        /*
         * !!! This is meant to be run on a new installation only !!!
         *
         * It will delete any preexisting users.
         *
         * ALWAYS BE CAREFUL!
         *
         * */

        //Delete all the relevant tables and caches.
        $this->command->info('truncating users, roles and permissions tables');
        app()[\Spatie\Permission\PermissionRegistrar::class]->forgetCachedPermissions();

        DB::statement('SET FOREIGN_KEY_CHECKS = 0;');
        DB::statement('truncate table users;');
        DB::statement('truncate table roles;');
        DB::statement('truncate table permissions;');
        DB::statement('truncate table model_has_permissions;');
        DB::statement('truncate table model_has_roles;');
        DB::statement('truncate table role_has_permissions;');
        DB::statement('SET FOREIGN_KEY_CHECKS = 1;');

        //Collect setting from the configuration script in configs/role_seeder.php
        $roles = config('role_seeder.roles');
        $objects = config('role_seeder.objects');
        $permissions_map = collect(config('role_seeder.permissions_map'));
        $role_has_permission = config('role_seeder.role_has_permission');


        //Create all the permissions with a common naming convention
        foreach ($objects as $object_name)
        {
            foreach ($permissions_map as $permission_key => $permission_value)
            {
                $name = $permission_value . ' ' . $object_name;
                Permission::create(['name' => $name]);
                $this->command->info('Creating Permission: ' . $name);
            }
        }

        //Create each role
        foreach ($roles as $role) {
            $this->command->info('Creating Role: '. $role);
            $new_role = Role::create(['name' => $role]);

            //Instead of copying a lot of letters in the config script, an empty array means ALL permissions
            if($role_has_permission[$role] === [])
            {
                //this is the superadmin
                $this->command->warn('Granting Role: '. $role .' all permissions.');
                $new_role->givePermissionTo( Permission::all() );
            }
            else
            {
                //givePermission to each role as prescribed in the config
                foreach($role_has_permission[$role] as $object => $perms)
                {
                    $perms_ary = explode(",", $perms);
                    foreach($perms_ary as $perm)
                    {
                        $name = $permissions_map[$perm] . ' ' . $object;
                        $new_role->givePermissionTo( $name );
                        $this->command->info('Granting Role: '. $role .' permission: '. $name);
                    }
                }

            }

            //this creates a user and grants the role so you can sign in and test things out.
            $data = [
                'name' => $role,
                'email' => $role . '@yourwtvr.com',
                'password' => Hash::make('secret')
            ];
            $user = User::create($data);
            $user->assignRole($role);

        }
    }
}
</pre>

I create a configuration script in the config directory. It looks like this.

config/role_seeder.php

<pre data-mode="php" data-theme="monokai" data-fontsize="14" data-lines="Infinity" class="wp-block-simple-code-block-ace">&lt;?php
return [
    'roles' => [
        'superadmin', 'moderator', 'user', 'guest'
    ],

    'objects' => [
        'user',
        'post',
        'comment',
        'tag',
        'permission',
    ],

    'permissions_map' => [
        'va' => 'view any',
        'v' => 'view',
        'c' => 'create',
        'u' => 'update',
        'd' => 'delete',
        'fd' => 'force delete',
        'r' => 'restore',
        'a' => 'add',
        'at' => 'attach',
        'dat' => 'detach',
        'ata' => 'attachAny',
    ],

    'role_has_permission' => [
        'superadmin' => [], // this will grant all permissions
        'moderator' => [
            'user' => 'va,v,c,u',
            'post' => 'va,v,c,u,d,fd,r',
            'comment' => 'va,v,c,u,d,fd,r,a',
            'tag' => 'va,v,c,u,d,fd,r,at,dat'
        ],
        'user' => [
            'post' => 'va,v,c,u,d,fd',
            'comment' => 'va,v,c,u,d,fd,a',
            'tag' => 'va,v,at,dat',
        ],
        'guest' => [
            'post' => 'va,v',
            'comment' => 'va,v,c,a'
        ],
    ]
];
</pre>

To finish up seeding your authorization structure follow this up with:

<pre class="wp-block-code"><code>php artisan config:cache
php artisan db:seed --class=RoleSeeder</code></pre>

You now have a few users with the corresponding roles. You can login and check how things look. Loosen restrictions where you need to, tighten restrictions where you can.

#### So What About The Gates?!

Right. Laravel is really a beautiful framework. I have been using it since v4.1 and have taken it with me to every job and project since. The creators have taken a deep dive to make programming easier and even &#8230; fun. So much so that Laravel feels like its own language on top of PHP. It reminds me of ObjectiveC, a language where the underlying language, C, is unrecognizable. So if you aren&#8217;t using Gates yet, don&#8217;t worry, the framework is. 

In the case of Laravel Nova, creating all of these permissions and roles really makes your life easier. Nova is sniffing for authorizations every time you click anything. It is doing this using Policies. Let&#8217;s create a Policy for App\Post.

<pre class="wp-block-code"><code>php artisan make:policy PostPolicy</code></pre>

<pre data-mode="php" data-theme="monokai" data-fontsize="14" data-lines="Infinity" class="wp-block-simple-code-block-ace">&lt;?php

namespace App\Policies;

use App\User;
use Illuminate\Auth\Access\HandlesAuthorization;

class PostPolicy
{
    use HandlesAuthorization;

    public function viewAny(User $user){ return $user->can('view any post'); }
    public function view(User $user){ return $user->can('view post'); }
    public function create(User $user){ return $user->can('create post'); }
    public function update(User $user){ return $user->can('update post'); }
    public function delete(User $user){ return $user->can('delete post'); }
    public function forceDelete(User $user){ return $user->can('force delete post'); }
    public function restore(User $user){ return $user->can('restore post'); }
    public function add(User $user){ return $user->can('add post'); }
    public function attach(User $user){ return $user->can('attach post'); }
    public function detach(User $user){ return $user->can('detach post'); }
    public function attachAny(User $user){ return $user->can('attachAny post'); }

}</pre>

Making a policy for all the objects is boilerplate. There&#8217;s an abstraction to be done here, but I am going to relax the problem and just copy and paste a little bit. Once you&#8217;re done you can go back and read the Laravel documentation on Authorization and it will make a lot more sense. You will be able to:

<pre data-mode="php" data-theme="monokai" data-fontsize="14" data-lines="Infinity" class="wp-block-simple-code-block-ace">&lt;?php

Gate::before(function ($user, $ability) {
    if ($user->hasRole('superadmin')) {
        return true;
    }
});
</pre>

Or

<pre data-mode="php" data-theme="monokai" data-fontsize="14" data-lines="Infinity" class="wp-block-simple-code-block-ace">&lt;?php

/**
 * Register any authentication / authorization services.
 *
 * @return void
 */
public function boot()
{
    $this->registerPolicies();

    Gate::define('update-post', 'App\Policies\PostPolicy@update');
}
</pre>

and even

<pre data-mode="php" data-theme="monokai" data-fontsize="14" data-lines="Infinity" class="wp-block-simple-code-block-ace">&lt;?php

namespace App\Providers;

use Illuminate\Support\Facades\Gate;
use Illuminate\Foundation\Support\Providers\AuthServiceProvider as ServiceProvider;

class AuthServiceProvider extends ServiceProvider
{
    /**
     * The policy mappings for the application.
     *
     * @var array
     */
    protected $policies = [
        'App\User' => 'App\Policies\UserPolicy',
        'App\Post' => 'App\Policies\PostPolicy',
        'App\Comment' => 'App\Policies\CommentPolicy',
        'App\Tag' => 'App\Policies\TagPolicy',
        'App\Permission' => 'App\Policies\PermissionPolicy',
    ];
    
    /**
     * Register any authentication / authorization services.
     *
     * @return void
     */
    public function boot()
    {
        $this->registerPolicies();

        //
    }    

        
        </pre>

and you are good to go. Now when the wrong kind of user tries an action on the wrong kind of object, Laravel with throw an exception in the form of a pretty 403 screen.

In Laravel Nova, after registering these policies, Nova is checking them relentlessly. Play with this code in your Nova Resources. Tweak your permissions and navigation so your Roles can have their own distinct looking interfaces. 

<pre data-mode="php" data-theme="monokai" data-fontsize="14" data-lines="Infinity" class="wp-block-simple-code-block-ace">&lt;?php    

    /**
     * Indicates if the resource should be displayed in the sidebar.
     *
     * @param Request $request
     * @return
     */
    //public static $displayInNavigation = true;
    public static function availableForNavigation(Request $request)
    {
        return $request->user()->can('view any post');
    }
    </pre>

Easy! **?**