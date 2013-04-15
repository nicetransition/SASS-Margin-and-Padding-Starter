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
* 02.14.13 - Updates for *"-sides", this was originally missing in the Initial Release. Also updated the initial size from 40px to 20px, for the example.
* 04.15.13 - Updates to documentation and a few whitespace spots removed. Moved media query to top of the file. Introduced official versions and branches. Welcome `v1.1`


### Ect

`@import` "spacing.scss" in your global *.scss file OR just put the following code within your global *.scss file.
<pre>
@import "spacing";
</pre>