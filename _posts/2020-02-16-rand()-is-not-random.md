---
layout: post
author: Bas
---
In [my second posts here](https://bas.rel.nl/2020/01/21/Raspberry-Pi-Photowall.html){:target="_blank"} I described my 3*2 screen 'piwall' setup, used 
as a big 'photo-frame'.

![image](/assets/images/piwall.jpg)  

However... I Noticed something was 'off' with the 'randomness' of the displayed pictures!

Seeing the same photo's on a dayly basis, over and over again? While using a 'library' of about +25.000 pictures? Something surely had to be wrong?! 

Ignored this for a long time, until this really started nagging me a lot! 

Eventually I realized the 'random slideshow' code-part for this thing, was written by me in PHP... Some ~12 years ago!

So the PHP script running on my 'php-pi-photowall webserver' was using the old PHP rand() function; Quite common to use in the pre-PHP 5.x days. 

However, rand() was replaced by 'mersenne twister' mt_rand() and eventually random_int() was introduced during al those years. 

Even in PHP 7.2 the mt_rand() function (an alias for rand() since 7.1) had received a fix for a modulo bias bug.



Lessons learned: 

* Don't re-use your old code, without looking at how the language built-in functions-used have evolved over the years!

* Randomness is a *very complicated* subject in computing!! 

* Your eyes and brain are really good at spotting non-randomness in a picture slide-show! :-)  


 
 
