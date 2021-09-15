
# Using Webp for splash image

Webp is image format (based on the VP8 video format) that supports lossy and lossless compression, as well as animation and alpha transparency. WebP generally has better compression than JPEG, PNG and GIF and is designed to supersede them.

In that example:
 - png: 873 Kb (100%)
 -  webP: 336 Kb (38.5%)

Webp supported in most of current browsers https://caniuse.com/webp.
But it better to add fallback to png, for some old browsers.

There are 2 ways to add wepb in defold.

 1. No fallback (simple)
 2. With fallback

## No fallback
1)Select splash image in game.project. 
 - it will not show webp images in list, but if you write path it will work

