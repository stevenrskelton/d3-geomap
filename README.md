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

Attribute			| Type			| Default		| Description
---					| ---			| ---			| ---
`selected`	 		| *object*		| `null`		| keys are region id, values are either a CSS color, or a __region element__
`hover`				| *object*		| `null`		| Region hovered over by user pointer
`data`				| *object*		| `null`		| keys are region id, values are arbitrary data to be associated with region
`map`				| *string*		| world			| Acceptable values are `world` and `usa`, will render world and USA maps respectivily.

Event				| Value			| Description
---					| ---			| ---
`clicked`			| *object*		| Region clicked by user

## Region Elements

Regions are JSON objects describing sections of the topology, and they must be uniquely keyed.
For the world map the key is the [ISO 3166-1 alpha-3](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-3) country code.
They can have arbitrary properties, but there are a few special properties reserved for internal use.
`color` is used to describe the background color, and it is a standard CSS color.

## Todo

- fix bugs
- expose more DataMaps functionality
- D3 and DataMaps dependencies using bower
- different maps (USA, etc)
- __Internet Explorer is completely broken__

## History

For detailed changelog, check [Releases](https://github.com/stevenrskelton/d3-datamaps/releases).

## License

[MIT License](http://opensource.org/licenses/MIT) © Steven Skelton