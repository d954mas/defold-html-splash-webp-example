
# Using Webp for splash image

Webp is image format (based on the VP8 video format) that supports lossy and lossless compression, as well as animation and alpha transparency. WebP generally has better compression than JPEG, PNG and GIF and is designed to supersede them.

In that example:
 - png: 873 Kb (100%)
 -  webP: 336 Kb (38.5%)

Webp supported in most of current browsers https://caniuse.com/webp.
But it better to add fallback to png, for some old browsers.


For converting png to webp i use https://image.online-convert.com/convert-to-webp 

There are 2 ways to add wepb in defold.

 1. No fallback (simple)
 2. With fallback


If you like that. You can support me on patreon.
It will help me make more items for defold.

[![](https://c5.patreon.com/external/logo/become_a_patron_button.png)](https://www.patreon.com/d954mas)

[!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/d954mas)



## No fallback
1)Select splash image in game.project. 
 - it will not show webp images in list, but if you write path it will work

## With fallback
You will need to make changes in engine-template and css to make fallback working.

1)Make a bundle resources folder. (bundle/web) Add it in game.project. 
2)Put loading.webp and loading.png in bundle/web
3)You need detect is browser support webp or not. I use [modernizr](https://modernizr.com/docs).
 bundle/web/modernizr-custom.js
4)You need custom index.html and css. Copy engine_template.html and dark_theme.css from builtins.
5)In engine_template.html add modernizr

    <script id='modernizr' type='text/javascript' src="modernizr-custom.js"></script>

6)In dark_theme.css

 - remove default splash image logic
  `{{#DEFOLD_SPLASH_IMAGE}}
		background-image: url("{{DEFOLD_SPLASH_IMAGE}}");
{{/DEFOLD_SPLASH_IMAGE}}
{{^DEFOLD_SPLASH_IMAGE}}
		background-size: 70%;
		background-image: url("...");
{{/DEFOLD_SPLASH_IMAGE}}`
 - add new logic (.no-webp and .web is from modernizr)
.no-webp .canvas-app-canvas {  
  background-image: url("loading.png");  
}  
  
.webp .canvas-app-canvas{  
  background-image: url("loading.webp");  
}


 
