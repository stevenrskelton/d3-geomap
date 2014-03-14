&lt;d3-datamaps&gt;
=============

Polymer Web Component for geographic topology visualization.

This is a web component wrapper to another SVG map visualization library [DataMaps](http://datamaps.github.io/) by Mark DiMarco.
It uses the popular [D3 Data-Driven Documents](http://d3js.org/) to handle low level HTML and SVG rendering.

Features will mirror DataMaps features, however the format for interaction will be adjusted to follow the web component paradigm. 
This means significant simplifications will be made to provide an improved usability for the majority of users.  Advanced use cases may find 
a web component encapsulation too restrictive, and those uses are outside the scope of this project.

Maintained by [Steven Skelton](https://github.com/stevenrskelton)

## Live Demos
 
> [World Countries Map](http://files.stevenskelton.ca/d3-datamaps/examples/world.html)

> [USA State Map](http://files.stevenskelton.ca/d3-datamaps/examples/usa.html)

> [Backgrounds](http://files.stevenskelton.ca/d3-datamaps/examples/backgrounds.html)

> [Mouse Control](http://files.stevenskelton.ca/d3-datamaps/examples/mouse.html)

> [Multi-Select](http://files.stevenskelton.ca/d3-datamaps/examples/multiselect.html)

> [Themes and Styling](http://files.stevenskelton.ca/d3-datamaps/examples/themes.html)

> [Sizing and Aspect Ratio](http://files.stevenskelton.ca/d3-datamaps/examples/size.html)

> [Zoom and Widths](http://files.stevenskelton.ca/d3-datamaps/examples/zoom.html)

## Usage

1. Import Web Components' polyfill, and a D3 library:

	```html
	<script src="//cdnjs.cloudflare.com/ajax/libs/polymer/0.2.0/platform.js"></script>
	<script src="//cdnjs.cloudflare.com/ajax/libs/polymer/0.2.0/polymer.js"></script>
	<script src="//cdnjs.cloudflare.com/ajax/libs/d3/3.4.2/d3.min.js"></script>
	```

2. Import Custom Element:

	```html
	<link rel="import" href="src/d3-datamaps.html">
	```

3. Start using it!

	```html
	<d3-datamaps></d3-datamaps>
	```

## Options

Attribute			| Type			| Default		| Description
---					| ---			| ---			| ---
`data`				| *object*		| `null`		| keys are region id, values are arbitrary data to be associated with region
`hover`				| *object*		| `null`		| Region hovered over by user pointer
`hoverTemplate`		| *function*	| `null`		| Function with `geometry` and `data` parameters, returns HTML `string` to display in region hover-over
`map`				| *string*		| world			| Acceptable values are `world` and `usa`, will render world and USA maps respectivily.
`multiselect`		| *boolean*		| `false`		| If true, `selected` is automatically populated by user clicks
`theme`				| *object*		| _default_		| CSS styles to apply to map, see __Themes__
`selected`	 		| *object*		| `null`		| keys are region id, values are a CSS color.  Also supports an `array` if region ids where `defaultSelectedFill` color is assumed
`zoom`	 			| *object*		| _default_		| Center of map and size, see __Zoom__
`rootDirectory`		| *string*		| ../src/		| Hack to get relative directory for topology maps from where web component is included


Event				| Value			| Description
---					| ---			| ---
`clicked`			| *object*		| Region clicked by user

## Region IDs

Region IDs are used to uniquely identify regions, and are the keys to both the `data` and `selected` object maps.
The world country map uses 3 letter [ISO 3166-1 alpha-3](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-3) country codes,
while the USA state map uses 2 letter [ANSI standard INCITS 38:2009](http://en.wikipedia.org/wiki/List_of_U.S._state_abbreviations) codes.

## Themes

The map is capable to be styled via the `theme` attribute, which has the following properties:

Attribute				| Type		| Default					| Description
---						| ---		| ---						| ---
`defaultFill`	 		| *color*	| #ABDDA4					| Regular fill for all land regions
`defaultSelectedFill`	| *color*	| #FBB917					| Fill for selected regions if `selected` is an array
`backgroundColor`		| *color*	| transparent				| Background fill for map (water)
`borderWidth`			| *int*		| 1							| Border width (px) for regular regions
`borderColor`			| *color*	| #FDFDFD					| Border color for regular regions
`highlightFillColor`	| *color*	| #FC8D59					| Fill for highlighted/hover region
`highlightBorderColor`	| *color*	| rgba (250, 15, 160, 0.2)	| Border color for highlighted/hover region
`highlightBorderWidth`	| *int*		| 2							| Border width (px) for highlighted/hover region
`cursor`				| *cursor*	| pointer					| See the W3C Spec http://www.w3.org/wiki/CSS/Properties/cursor
`backgroundImage`		| *image*	| none						| See the W3C Spec http://www.w3.org/TR/css3-background/#the-background-image

## Zoom

The map can be centered and scaled using the `zoom` object, which has the following properties:

Attribute				| Type		| Default					| Description
---						| ---		| ---						| ---
`x`	 					| *float*	| 0							| Horizontal offset from center in °, range [-180,180]
`y`						| *float*	| 0							| Vertical offset from center in °, range [-90,90]
`scale`					| *float*	| 100						| Percent to zoom, 100% = 1x
`zoom`					| *boolean*	| false						| Enable mouse zoom using scroll-wheel
`zoomScale`				| *float*	| 0.1						| Percent to increment/deincrement on mouse zoom
`pan`					| *boolean*	| false						| Enable mouse pan on drag

## Backgrounds

Backgrounds are applied to a `div[id="container"]` that contains the `svg` map element.  Changing the __zoom__ will automatically 
adjust the background to be in the appropriate position.

The __world__ topology is a standard [Equirectangular projection](http://en.wikipedia.org/wiki/Equirectangular_projection).

The __usa__ topology is an [Albers USA projection](http://bl.ocks.org/mbostock/4090848).

## Todo

- fix out of bound errors with mouse controlled pan, scroll-wheel zoom
- optimize Firefox performance on mouse zoom and pan
- hover template using Template
- better built-in background interface
- better transitions between zoom changes
- disabled regions
- different projections, see [D3 Geo Projections](https://github.com/mbostock/d3/wiki/Geo-Projections)
- test responsiveness of bound data attributes
- expose more DataMaps functionality (bubbles, arcs)
- D3 and DataMaps dependencies using bower
- maybe: different maps (provinces/states, US districts, etc)
- __Internet Explorer is a work in progress__

## History

For detailed changelog, check [Releases](https://github.com/stevenrskelton/d3-datamaps/releases).

## License

[MIT License](http://opensource.org/licenses/MIT) © Steven Skelton