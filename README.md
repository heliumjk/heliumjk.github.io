# Helium Jekyll
## A new Bootstrap 4 theme

## The project is no longer mantained

<a href="https://jekyll-themes.com">
    <img src="https://img.shields.io/badge/featured%20on-JT-red.svg" height="20" alt="Jekyll Themes Shield" >
</a>

Helium is a fast, modern and configurable [Jekyll](http://jekyllrb.com/) theme with some tricks up it's sleeve. It has a live theme switcher and it's main blog layout display prominent hero images for posts with colored overlays and nice animations.

[Bootstrap theme source](https://uideck.com/products/helium-ui-kit/)

![helium sample](https://raw.githubusercontent.com/heliumjk/heliumjk.github.io/master/assets/images/helium-screenshot.jpg)
![helium theme](https://raw.githubusercontent.com/heliumjk/heliumjk.github.io/master/assets/images/helium-screenshot1.jpg)

## Features
Though minimalistic-looking by nature, dactl is easily configurable and includes quite a lot of niceties:

Main features:
* [Bootstrap 4](https://v4-alpha.getbootstrap.com/)
* [Font Awesome](http://fontawesome.io/)
* 100+ UI Blocks
* Responsive design

Jekyll-specific features:
* Fully compatible with Jekyll 3.x and GitHub Pages
* SEO optimized
* [Google Analytics](https://www.google.com/analytics/) support
* [Google AdSense](https://www.google.com/adsense/start/) support
* [Disqus](https://disqus.com/) comments support

Other features:
* Blog page
* Landing page samples
* Tags functionality and tags pages
* Link posts functionality
* Mobile slider scrolling
* Emoji support ⚡️⚡️⚡️ by copy paste from [getemoji](http://getemoji.com/)

Some of the features listed above can be easily configured or disabled by you.

## Information about Helium
At it's core, dactl is a forked version of [sentenza](https://github.com/sentenza/jekyll-material-design) but it has been almost entirely rewritten from scratch.  
I have just started my journey in the world of web development, learning new things on the way.  
Looking for a way to put my newly acquired skills to test I found Jekyll and I quickly realized that it's going to be a good learning experience since I don't like building 'dummy' projects.  
I've built this theme as a way to develop my skills further.

You can find credits at the bottom of this Readme file.  
**All** feedback is welcome, both positive and negative.

## Installation
### Running locally
Assuming you've got Jekyll [installed](https://jekyllrb.com/docs/installation/), clone or download this repo, `cd` into the folder and run `jekyll serve`.

### Hosting on GitHub
Fork this repo and rename it to `yourusername.github.io`... and edit the `_config.yaml` file whit your github address and your links (such as social media username, email, name, ecc.)!  
Your new helium-themed Jekyll blog should be up and running at yourusername.github.io.  


## Additional information about some features
### Hero images and blog layout
Liquid 'script' which is used to append correct hero image and overlay color as set in post YAML Front matter was written by me and while it's really basic it functions properly.  
You can read more about it and see the code in `include/utils/hero.html`.

#### Tags & Tags Pages
Tags and tag pages are supported by using Jekyll's native collections functionality.  

## Credits
### Resources used
- [Helium B4](https://uideck.com/products/helium-ui-kit/)
- [Font Awesome](http://fontawesome.io/)
- [Bootstrap 4](https://v4-alpha.getbootstrap.com/)

### Inspiration and thoughtful code-jacking
Inspiration and bits of things listed below are present inside dactl's code:
- [Daktilo](https://github.com/kronik3r/daktilo) - dactl is based on Daktilo and inherits it's one-column layout.
- [Hydejack](https://github.com/qwtel/hydejack/) - I've learned a lot about Jekyll when I took apart [@qwtel](https://github.com/qwtel/)'s excellent fork of [Hyde](https://github.com/poole/hyde) theme. I embraced his more partials = everything is easier to edit policy. Hydejack theme gave me an idea on how to create hero images liquid scripting, loading google fonts and using rem's/em's and more.
- [Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes) - This guy makes awesome themes and writes a lot about Jekyll and it's more obscure use cases on his blog, [Made Mistakes](https://mademistakes.com). Looking through his theme's code - Minimal Mistakes in particular - gave me lot of information about how to build a robust theme and how to make it configurable within `_config.yml`
- [Trophy](https://github.com/thomasvaeth/trophy-jekyll) - Link border slide animation SASS mixin which I slightly modified to be able to easily change the direction of the animation.
- Various blog posts about Jekyll and [Stackoverflow](https://www.stackoverflow.com) posts with useful [Liquid](https://github.com/Shopify/liquid) snippets.

## License
All parts of helium Jekyll theme are free to use and abuse under the open-source [MIT license](http://opensource.org/licenses/mit-license.php).

## TO DO
- [ ] Add Ads Block to home page 
- [ ] Minimize `.css` in `<head>` and all images for faster load times
- [ ] 404 page styles
- [ ] Create hightlight style for code parts

## Help out
Im [Ed Anisko](https://antoniotrento.github.io) and I'm looking for funds to be able to open my IT development company with many on-site projects, unfortunately they are hardly feasible without collaboration and an economic base.

If you want to contribute you can donate ethereum or bitcoin:
- [Donate Bitcoins](https://blockchain.info/address/1B9rDoFCndbsKXL9QiefUcUGUbJH9Y1i6M)
