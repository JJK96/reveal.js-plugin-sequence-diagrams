# JS Sequence Diagrams - Reveal.js Plugin

A plugin for [Reveal.js](https://github.com/hakimel/reveal.js) allowing to add Sequence Diagrams.

The sequence diagrams are generated by https://github.com/bramp/js-sequence-diagrams. (Website: https://bramp.github.io/js-sequence-diagrams/)

## Installation

### Build 
```npm run build```

### Copy
Copy the files inside the ```dist``` folder into the plugin folder of your reveal.js presentation, i.e. ```plugin/sequence-diagrams```.


### Dependencies
Add the plugins to the dependencies in your presentation, as below. 

```javascript
Reveal.initialize({
	// ...
	dependencies: [
		// ... 
		{ src: 'plugin/sequence-diagrams/webfont.js' },
		{ src: 'plugin/sequence-diagrams/snap.svg-min.js' },
		{ src: 'plugin/sequence-diagrams/underscore-min.js' },
		{ src: 'plugin/sequence-diagrams/sequence-diagram-min.js' },
		{ src: 'plugin/sequence-diagrams/sequence-diagrams-plugin.js' },
		// ... 
	]
});
```

Also import the CSS if you plan to use the hand drawn theme:
```html
<link href="plugin/sequence-diagrams/sequence-diagram-min.css" rel="stylesheet" />
```

## Configuration
The plugin can be configured by providing a sequencediagrams option containing an object with `theme`,  `useFragments` and `initialize` within the reveal.js initialization options.

```javascript
Reveal.initialize({
	// ...
	sequencediagrams: {
		  	theme: "simple", 
		  	useFragments: true, 
			initialize: (function(diagramContainer){ 
		    		console.log("Diagram rendered!");
			})
	 },
	 // ...	
```
### Configuration items
**theme**
You can configure `simple` or `hand`

**useFragments**
`true` registers all steps and notes as [Reveal.js Fragments](http://lab.hakim.se/reveal-js/#/fragments)

## Basic usage
The plugin searches for all HTML objects with class `sequence-diagram`. Then it uses the `innerText` of that element to build the sequence diagram.

**Example:**
```html
<script class="sequence-diagram" type="text/template" data-config-useFragments="true" data-config-theme="simple">
	Title: Here is a title
	A->B: Normal line
	B-->C: Dashed line
	Note right of A: He thinks \n about it
	C->>D: Open arrow
	D-->>A: Dashed open arrow
	Note left of D: He thinks \n about it
	A->A: Self
</script>	
```

The `data-config-*` attributes overrides the config from the reveal.js initialization options. But they are not required.
