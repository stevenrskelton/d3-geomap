&lt;d3-geomap&gt;
=============

Polymer Web Component for geographic topology visualization.

![Screenshot](https://raw.githubusercontent.com/stevenrskelton/d3-geomap/master/d3-geomap.jpg "Screenshot")

This is a web component wrapper to another SVG map visualization library [DataMaps](http://datamaps.github.io/) by Mark DiMarco.
It uses the popular [D3 Data-Driven Documents](http://d3js.org/) to handle low level HTML and SVG rendering.

Features will mirror DataMaps features, however the format for interaction will be adjusted to follow the web component paradigm. 
This means significant simplifications will be made to provide an improved usability for the majority of users.  Advanced use cases may find 
a web component encapsulation too restrictive, and those uses are outside the scope of this project.

Maintained by [Steven Skelton](https://github.com/stevenrskelton)

## Live Demos

> [World Countries Map](http://files.stevenskelton.ca/d3-geomap/d3-geomap/examples/world.html)

> [USA State Map](http://files.stevenskelton.ca/d3-geomap/d3-geomap/examples/usa.html)

> [Backgrounds](http://files.stevenskelton.ca/d3-geomap/d3-geomap/examples/backgrounds.html)

> [Markers](http://files.stevenskelton.ca/d3-geomap/d3-geomap/examples/markers.html)

> [Mouse and Touch Control](http://files.stevenskelton.ca/d3-geomap/d3-geomap/examples/mouse-touch.html)

> [Multi-Select](http://files.stevenskelton.ca/d3-geomap/d3-geomap/examples/multiselect.html)

> [CSS Styling](http://files.stevenskelton.ca/d3-geomap/d3-geomap/examples/css.html)


## Usage

1. Add the library using the Javascript package manager [Bower](http://bower.io/):

	```bower install --save d3-geomap```

2. Import Web Components' polyfill:

	```html
	<script src="bower_components/webcomponentsjs/webcomponents.min.js"></script>
	```

3. Import Custom Element:

	```html
	<link rel="import" href="bower_components/d3-geomap/d3-geomap.html">
	```

4. Start using it!

	```html
	<d3-geomap>
		<!-- add templates here -->
	</d3-geomap>
	```

## Options

Attribute			| Type			| Default		| Description
---					| ---			| ---			| ---
`data`				| *object*		| `null`		| keys are region id, values are arbitrary data to be associated with region
`hover`				| *object*		| `null`		| Region hovered over by user pointer
`map`				| *string*		| world			| Acceptable values are `world` and `usa`, will render world and USA maps respectivily.
`multiselect`		| *boolean*		| `false`		| If true, `selected` is automatically populated by user clicks
`theme`				| *object*		| _default_		| CSS styles to apply to map, _see_ [Themes](#themes)
`selected`	 		| *object*		| `null`		| keys are region id, values are a CSS color.  Also supports an `array` if region ids where `defaultSelectedFill` color is assumed
`projection`		| *object*		| _default_		| Center of map and size, _see_ [Projection](#projection)
`pan`				| *boolean*		| `false`		| Enable mouse/touch pan on drag
`zoom`				| *boolean*		| `false`		| Enable mouse scroll-wheel/touch pinch zoom
`hovertemplate`		| *function*	| `null`		| _See_ [hovertemplate](#hovertemplate)

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
`cursor`				| *cursor*	| pointer					| _See the W3C Spec_ [http://www.w3.org/wiki/CSS/Properties/cursor](http://www.w3.org/wiki/CSS/Properties/cursor)
`backgroundImage`		| *image*	| none						| _See the W3C Spec_ [http://www.w3.org/TR/css3-background/#the-background-image](http://www.w3.org/TR/css3-background/#the-background-image)

## Projection

The map can be centered and scaled using the `zoom` object, which has the following properties:

Attribute				| Type		| Default					| Description
---						| ---		| ---						| ---
`x`	 					| *float*	| 0							| Horizontal offset from center in °, range [-180,180]
`y`						| *float*	| 0							| Vertical offset from center in °, range [-90,90]
`scale`					| *float*	| 1.0						| Scale 1x = 100%
`zoomIncrement`			| *float*	| 0.1						| Percent to increment/deincrement on mouse zoom
`zoomScale`				| *float*	| 1.0						| Scale due to zoom, 1x = 100%
`panX`					| *float*	| 0							| Horizontal offset from center, in pixels
`panY`					| *float*	| 0							| Vertical offset from center, in pixels

## Backgrounds

Backgrounds are applied to a `div[id="container"]` that contains the `svg` map element.  Changing the __zoom__ will automatically 
adjust the background to be in the appropriate position.

The __world__ topology is a standard [Equirectangular projection](http://en.wikipedia.org/wiki/Equirectangular_projection).

The __usa__ topology is an [Albers USA projection](http://bl.ocks.org/mbostock/4090848).

### Templates

All templates must be nested inside the `<d3-geomap>` tag to be accessible to the polymer element.

Any filter used (eg: `sum` in a following example) must be a member of `PolymerExpressions.prototype`.
See the [Polymer Filters](#polymer-filters) section for more details.

As always, only a very limited subset of Javascript is allowed within `{{ }}` expressions.
See the [Polymer documentation](http://www.polymer-project.org/docs/polymer/expressions.html) on Expression syntax.

#### hoverTemplate

Renderer for what shows when a region is hovered over.

Template Variable		|	Description
---						|	---
`{{hover.id}}`			|	[RegionID](#region-ids) of region
`{{hover.name}}`		|	Name of region
`{{hover.data}}`		|	Custom user data assigned to region (_empty by_default_)

## History

For detailed changelog, check [Releases](https://github.com/stevenrskelton/d3-geomap/releases).

## License

[MIT License](http://opensource.org/licenses/MIT) © Steven Skelton