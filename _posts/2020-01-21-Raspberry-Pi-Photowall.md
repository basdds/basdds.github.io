---
layout: post
author: Bas
---
['php-pi-photowall'](https://github.com/basdds/php-pi-photowall){:target="_blank"} - A simple PHP script for displaying randomly-chosen pictures on my 6 PiWall nodes. 

![image](/assets/images/piwall.jpg)

**What is a 'piwall'??** 

In 2016 I've built a 3*2 'PiWall'; A grid of 6 old 19' Monitors, each having a Raspberry Pi behind it. 

This PiWall is capable of running the [Piwall](http://www.piwall.co.uk/){:target="_blank"} video software, open sourced in 2013.
The software enables you to 'split' a UDP multicast video stream, to different 'receiving' nodes. So multiple pi's + monitors can devide and display the same video source.

A [video](https://www.youtube.com/watch?v=Kru--U1kRy8){:target="_blank"} of what this piwall can do:  

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/Kru--U1kRy8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe><br/>

And how it was built, using some wood as frame and stand: [FB Photo album 'piwall'](https://www.facebook.com/bas.dds.nl/media_set?set=a.1429959373697741.1073741893.100000510777171&type=1&l=a61e0e0002){:target="_blank"}

![image](/assets/images/piwall2.jpg)

The video streaming is fun! However.. All Pi's also have a full (lightdm) desktop, with a web browser installed. Each Pi-Screen is running the [Ubuntu-Mate distro.](https://ubuntu-mate.org/raspberry-pi/){:target="_blank"}

I was looking for a easy way to show a collection of +25.000 pictures, ramdomly on each screen. Tried making this work with the [Linux framebuffer imageviewer](https://manpages.ubuntu.com/manpages/bionic/man1/fbi.1.html){:target="_blank"} but 'fbi' randomly crashed often, when used with a list of picture files this large.  

So eventually I used a PHP script that does something like: 

```
$pics_list = glob("/var/www/frame/photowall/*");
$length_list = count($pics_list);
$random_nr = random_int(0, $length_list-1);
$image = $pics_list[$random_nr];
... etc, etc 

>>> Output some html with a <img src="<?php echo $image; ?>"> + a meta-refresh.
``` 

And use the browser on all pi's for displaying my image collection. This proved to work very well for me!

Sharing is caring, so I've put this online: [Github repo for the Rasperry PI 'photowall' script](https://github.com/basdds/php-pi-photowall){:target="_blank"}

Little disclaimer: I'm not a php/html/js-coder @dayjob... So the only browser I've used/tested this on is Firefox! If you have comments or code suggestions? Click /whois ^^ for contact info, or leave me an issue on github!

Example 'website' using this script is: [https://www.mister-p.nl/](https://www.mister-p.nl/){:target="_blank"} - I really DO miss this little guy!... :-(  

**Usage:**

On any PHP capable webserver; download the repo in the documentroot of your webserver and create this folder structure:

```
/var/www/frame
/var/www/frame/photowall
```

I suggest using one of the Pi's on your local network, for running this webserver. For fast **local** content delivery. (I use Nginx + php-fpm on #wall1) 

Put your collection of pictures in the folder 'photowall' and the PHP script + jquery.min.js file in the main folder. (in this example /var/www/frame/ is my local webserver's DocumentRoot)

Then fire up your browser(s) to point it at your webserver + F-11! (or script this with xdotool) 

When cloning this repo, you'll only need the index.php and jquery.min.js file. The 'photowall' folder contains some example pictures, just for demonstration. 

==Update 16-02-20== 

I found that the rand() function was flawed on the (used distro provided) PHP version, running on my Pi's.. 

Replacing it with the random_int() function, increased the 'randomness' of the displayed pictures quite a bit! 
Without a noticable performance hit. (modified ^^)  

