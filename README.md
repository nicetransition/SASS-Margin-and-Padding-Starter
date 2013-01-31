SASS-Margin-and-Padding-Starter
===============================

SASS Padding and Margin Starter .SCSS is used to generate classes for margin and padding spaces in your project. Ideal for object-oriented CSS.

### Purpose

Used to generate margin and padding for your project. Ideal for object-oriented CSS.


### Setup

Requires [SASS](http://sass-lang.com/) 3.2.x

<pre>
$ cd {~path to directory~}/assets
$ sass --watch scss:css --style compressed
</pre>


### Release History

* 01.31.13 - Initial Release


### Ect

@import "spacing.scss" in your global *.scss file OR just put the following code within your global *.scss file.
<pre>
@import "spacing";
</pre>

MY PHILOSOPHY: 
Responsive Web Design (RWD) should use fixed sizes not percent for margin & padding. 
Ask yourself this, would a designer ever design a margin or padding to be 4.567px? Probably not... so you shouldn't output code that does that either.
I have OCD when it comes to margin and padding for design and UI development. Consistent spacing is design 101, pixels matter.
#OOCSSrulez #ilovemondrian