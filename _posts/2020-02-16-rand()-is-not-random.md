---
layout: post
author: Bas
---
A short story about PHP's rand(): 

In [my second posts here](https://bas.rel.nl/2020/01/21/Raspberry-Pi-Photowall.html){:target="_blank"} I described my 3*2 screen 'piwall' setup, used 
as a big 'photo-frame'.

![image](/assets/images/crypt.jpg)  

However... I Noticed something was 'off' with the 'randomness' of the displayed pictures!

Seeing the same photo's on a almost daily basis, over and over again? While using a 'library' of about +25.000 pictures? 
Never seeing some pictures I *knew* where in the colection??? Something surely had to be wrong! 

Ignored this for a long time, until this really started nagging me a lot! 

Eventually I realized the 'random slideshow' code-part for this thing, was written by me in PHP... Some 12 to 14 years ago!

So the PHP script running on my 'php-pi-photowall' (LTS Ubuntu-mate webserver, running PHP 5.x) was using the PHP rand() function. 

Using PHP rand() was quite common, in the PHP 4/5 days. However, rand() was flawed and replaced by 'mersenne twister' 
mt_rand(). But even in PHP 7.2 the mt_rand() function had received a fix for a modulo bias bug.

Eventually random_int() was introduced as the only function to generate 'cryptographically secure pseudo-random integers' in PHP7

So my lessons learned are: 

* Don't re-use your old code, without looking at how it's language built-in functions have evolved over the years!

* Randomness is a *very complicated* subject! 

* Your eyes and brain are *really good* at spotting non-randomness in a 6-screen picture slide-show!  

* 2do: Take a deeper dive into the HRNG capabilties of the Pi! [article on this](http://scruss.com/blog/2013/06/07/well-that-was-unexpected-the-raspberry-pis-hardware-random-number-generator/)
