---
layout: post
author: Bas
---
A simple PHP script, for displaying randomly-chosen pictures on my 6 PiWall nodes. 

[Github repo for the Rasperry PI 'photowall'](https://github.com/basdds/php-pi-photowall){:target="_blank"}

![image](/assets/images/piwall.jpg)

**About this Script** 

A few years ago, I've built a 3*2 'PiWall'; A grid of 6 old 19' Monitors, each having a Raspberry Pi behind it. 

This PiWall is capable of running the [Piwall](http://www.piwall.co.uk/){:target="_blank"} video streaming software. 

See [this youtube video](https://www.youtube.com/watch?v=Kru--U1kRy8){:target="_blank"} for what this 'piwall' can do. 

And how it was built, using some wood for a supporting frame :-) 

[FB Photo album 'piwall'](https://www.facebook.com/bas.dds.nl/media_set?set=a.1429959373697741.1073741893.100000510777171&type=1&l=a61e0e0002){:target="_blank"}

The video streaming is fun! However.. All Pi's also have a full desktop with a web browser. Each Pi-Screen is running the Ubuntu-Mate distro.

I was looking for a easy way to show a collection of (20k) pictures ramdomly on each screen, so I've made this PHP script.

**Usage** 

On any PHP capable webserver; download the repo in the documentroot, or create this (example) folder structure:

```
/var/www/frame
/var/www/frame/photowall
```

I suggest using one of the Pi's on your local network running this webserver; for faster content delivery.

Put your collection of pictures in the folder 'photowall' and the PHP script + jquery.min.js file in the main folder. (in this example /var/www/frame/ is my local webserver's DocumentRoot)

Then fire up your browser(s) to point it at your webserver + F-11!

When cloning this repo, you'll only need the index.php and jquery.min.js file. The 'photowall' folder contains some example pictures, just for demonstration. 
