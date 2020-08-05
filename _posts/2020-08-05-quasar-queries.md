---
title: 'Quasar Queries'
date: 2020-08-05T22:45:54-08:00
author: ed.anisko@gmail.com
layout: post
categories:
  - Quasar
  - Node
  - Setup
---
Adding alpaca api to a node project so I can buy a share of QQQ or AAPL. 

Its easy enough to use the alpaca CLI in a flat js file.  Next step is to add it to an application, add a few buttons and so on. 



Searched for:
- installing other packages into quasar
  - https://quasar.dev/app-extensions/development-guide/introduction#Handling-package-dependencies
  - no

- using other packages with quasar
  - https://forum.quasar-framework.org/topic/3597/importing-and-using-external-js-libraries-in-quasar
  - https://quasar.dev/app-extensions/tips-and-tricks/provide-a-directive

Read the code, specifically the comments in the .quasar folder.  They point to setting up a boot directive.   A link in the comments points to:
- https://quasar.dev/quasar-cli/cli-documentation/boot-files#Anatomy-of-a-boot-file
- 404

Searched quasar site for boot finally find:

https://quasar.dev/quasar-cli/boot-files#Anatomy-of-a-boot-file

A little more digging turend up:

https://medium.com/quasar-framework/adding-axios-to-quasar-dbe094863728

The idea finally clicked.

In terminal type:

```sh
$ quasar new boot alpaca-api      
```

This creates /boot/alpaca-api.js

```js
const Alpaca = require('@alpacahq/alpaca-trade-api')

const alpacaInstance = new Alpaca({
  keyId: 'XXXXXXXXXXXXXXXXX',
  secretKey: 'XXXXXXXXXXXXXXXXXX',
  paper: true,
  usePolygon: false
})

export default async ({ Vue }) => {
  Vue.prototype.$alpaca = alpacaInstance
}

export { alpacaInstance }

```

in /quasar.conf.js add alpaca-api to the boot array:
```
    // app boot file (/src/boot)
    // --> boot files are part of "main.js"
    // https://quasar.dev/quasar-cli/boot-files
    boot: [
      'alpaca-api',
      'axios'
    ],

```


Then change /src/App.vue
```js
<template>
  <div id="q-app">
    <router-view />
  </div>
</template>
<script>

import { alpacaInstance } from 'boot/alpaca-api'

export default {
  name: 'App',
  mounted () {
    console.log(alpacaInstance.getAccount())
  }
}
</script>
```



Looks like its working.

