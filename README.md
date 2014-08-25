# Unit Space

**NOTE:** STILL A LOT OF WORK TO DO FOR README. I still need to do details on using the `@mixin` and cleaning this up for use. 

======


When creating an interface one of the most parts is spacing (`margin` and `padding`). Consistent units are vital for unity, balance, rhythm of your web applications. *Unit Space* is a foundation to generate create consistent spacing for your projects, no matter how many variations may be required in your system.


*Unit Space* is built in Sass 3.3.x to provide you the most flexibility and ease of maintainability.

----


## Generate Units

Within "**_unit_space__variables.scss**" there is a map data structure called `$units`. This map is used to generate custom outputs of units and disable output of compiled selectors.

The default output is to generate selectors for margin and padding that are default value, 2 times the default value, and half the default value. Within "_unit_space__variables.scss", you can update the default value by changing the value in `$units__default-unit`. Each unit has the ability to be updated at `@media` query, default can be overwritten by changing `$units__default-breakpoint`.

### Map Data Structure

There are two object maps that can live within `$units`, these two objects are **`padding`** and **`margin`**. Neither are required but these two options are to organize margin vs. padding. Within these objects you can generate new Sass map object with options that fit your needs.

````
$units: (
	"padding": (
		// options for padding output here
	),
	"margin": (
		// options for margin output here
	)
);
````

If using `padding` and/or `margin`, they do require to have their first variation to be called "**default**".

### Map Object Options

* "**selector-name**": *String* (no spaces and can't start with a *Number*). Optional. Used to change output selector name.
* "**selector-suffix**": *String* (no spaces). Optional. This is appended to the end of the output selector
* "**media-query-max**": *Number*. Optional. Uses `@media screen (max-width: "this value"){}`
* "**unit--media-query-max**": *Number*. Optional; Required when `media-query-max` is used. Is applied unit to `variation` options within the media query. Fallback unit is `unit`.
* "**media-query-min**": *Number*. Optional. Uses `@media screen (min-width: "this value"){}``
* "**unit--media-query-min**": *Number*. Optional; Required when `media-query-min` is used. Is applied unit to `variation` options within the media query. Fallback unit is `unit`.
* "**unit**": Required. *Number*. Required. Default unit. Is fallback unit for `unit--media-query-min` and `unit--media-query-max` when `media-query-min` and `media-query-max` are used and no unit is applied.
* "**variations**": Sass Map. Required. Contains the variations of output properites.
  * "**base**": Options: `true` | `false` | `short`. Required. Outputs default unit. When value is `short` this key is used to output `padding` and `margin` property's shorthand.
  * "**top**": *Boolean*. Required. Outputs variation of property (`padding-top`, `margin-top`)
  * "**right**": *Boolean*. Required. Outputs variation of property (`padding-right`, `margin-right`)
  * "**bottom**": *Boolean*. Required. Outputs variation of property (`padding-bottom`, `margin-bottom`)
  * "**left**": *Boolean*. Required. Outputs variation of property (`padding-left`, `margin-left`)

If `variations` is set to `false`, the output will be a Sass [%placeholder selector](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#placeholder_selectors_). If set to `true`, both compiled selectors and %placeholders will be available to use.

## Compiled Output
Showing in an example below, comment after shows output

````
...
		"two-times": (
			"suffix": "--2x",
			"media-query-max": $units__default-breakpoint, 
			"unit--media-query-max": $default-unit, 
			"media-query-min": $units__default-breakpoint,
			"unit--media-query-min": $default-unit * 2,
			"unit": $default-unit * 2,
			"variations": (
				"base": true, // %padding--2x, .padding--2x
				// "base": false, // %padding--2x
				"top": true, // %padding-top--2x, .padding-top--2x
				// "top": false, // %padding-top--2x
				"right": true, // %padding-right--2x, .padding-right--2x
				// "right": false, // %padding-right--2x
				"bottom": true, // %padding-bottom--2x, .padding-bottom--2x
				// "bottom": false, // %padding-bottom--2x
				"left": true // %padding-left--2x, .padding-left--2x
				// "left": false, // %padding-left--2x
			)
		),
...
````

### Custom Selector Output

````
...
		"two-times": (
			"suffix": "--2x",
			"unit": $default-unit * 2,
			"variations": (
				"base": true, // %padding--2x, .padding--2x
				// "base": false, // %padding--2x
				"top": true, // %padding-top--2x, .padding-top--2x
				// "top": false, // %padding-top--2x
				"right": true, // %padding-right--2x, .padding-right--2x
				// "right": false, // %padding-right--2x
				"bottom": true, // %padding-bottom--2x, .padding-bottom--2x
				// "bottom": false, // %padding-bottom--2x
				"left": true // %padding-left--2x, .padding-left--2x
				// "left": false, // %padding-left--2x
			)
		),
...
````

````
...
		"unique-identifier-name-here": (
			"selector-name": "unit",
			"suffix": "--half",
			"unit": $default-unit / 2,
			"variations": (
				"base": true, // %unit--half, .unit--half
				"top": true, // %unit-top--half, .unit-top--half
				"right": true, // %unit-right--half, .unit-right--half
				"bottom": true, // %unit-bottom--half, .unit-bottom--half
				"left": true // %unit-left--half, .unit-left--half
			)
		),
...
````