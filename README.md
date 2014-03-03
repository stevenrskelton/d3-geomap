&lt;d3-datamaps&gt;
=============

Polymer Web Component for geographic topology visualization.

This is a web component wrapper to another SVG map visualization library [DataMaps](http://datamaps.github.io/) by Mark DiMarco.
It uses the popular [D3 Data-Driven Documents](http://d3js.org/) to handle low level HTML and SVG rendering.

Features will mirror the DataMaps features, however the format for interaction will be adjusted to follow the web component paradigm. 
This means significant simplifications will be made to improve the usability for the majority of users.  Advanced use cases may find 
the web component encapsulation too restrictive, and it may be necessary for them to interact with the DataMaps library directly.

Maintained by [Steven Skelton](https://github.com/stevenrskelton)

## Live Demos
 
> [World Map](http://files.stevenskelton.ca/d3-datamaps/examples/world.html)

## Usage

1. Import Web Components' polyfill:

	```html
	<script src="//cdnjs.cloudflare.com/ajax/libs/polymer/0.2.0/platform.js"></script>
	<script src="//cdnjs.cloudflare.com/ajax/libs/polymer/0.2.0/polymer.js"></script>
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

Attribute			| Options		| Default		| Description
---					| ---			| ---			| ---
`selected`	 		| *array*		| `[]`			| ISO 3166-1 alpha-3 country codes of selected countries
`hover`				| *object*		| `null`		| Region hovered over by user pointer
`width`				| *int*			| 425			| Size in pixels to make map.  Height is automatically calculated.

## Todo

- make API more usable
- fix bugs
- expose more functionality
- D3 and DataMaps dependencies using bower
- different maps (USA, etc)
- __Internet Explorer is completely broken__

## History

For detailed changelog, check [Releases](https://github.com/stevenrskelton/d3-datamaps/releases).

## License

[MIT License](http://opensource.org/licenses/MIT) © Steven Skelton