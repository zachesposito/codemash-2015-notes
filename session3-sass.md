# Getting Sassy with Css
Julie Cameron

- Articulate

## Why Sass:
	- Bare CSS is great but harder and harder to maintain
		- tedious and repetitive
		- low features by design - adoptibility

	- DRY
		- values, styles, and selectors
		- variables
	- Increased maintainability, decreased complexity, more modular

	- Extension and Preprocessor
		- SassScript Language, SassScript Interpreter
		- .scss and .sass

## Workflow
	- --watch does not compile first, it only starts watching
	- --style
		- default - ending curlies are crunched
		- expanded - normal css
		- compact - each selector one line
		- compressed - minified

	- Sourcemap
		- get to source from chrome

	- ** Gitter.im - git-based chat **

## Basic Features
	### Nesting
		- GOTCHYA: don't nest the crap out of everything. Affects specificity.
		- & 
			- can be combined with strings, for approaches like BEM
				- e.g. .module { &--modifier{}}
			- also can access & as a string? not sure why that's useful though

	### Imports & Organization
		- import during compilation!
		- _partials won't be compiled on their own (e.g. when doing a whole directory)
		- can make partials called _all to aggregate 
		- can comma-separate for DRYer

	### Variables
		- Numbers, strings, colors, lists, booleans, null, maps
		- Guarded Assignment - !default
			- if not already defined make it this
		- They do have scope! thought so
			- Including global overrides in a selector, unless !global flag
		- Interpolation
			-stick onto/into other strings like classes, properties, or values

		- ** PROTIP - Modular Naming **
			- Give colors descriptive names, then assign descriptive names to functional names
			- e.g. $white: #fff; $header-background: $white;

	### Math
		- division is tricky since bare CSS allows / as separator
			-ways to trigger explicitly
		- bunch o helper functions
		- can do on color

	### Color utilities
		- functions for conversion, manipulation, etc
		- sassme good for previewing
		- [jackiebalzer.com/color](jackiebalzer.com/color)

------------------------------------------

## Next level
	### Mixins
		- best used with arguments, otherwise you're just duplicated styles in the output
		- can have default args
		- named arguments or arguments by order
		- Interpolation

		- icon mixin
		- mixin to create shapes (like triangle)

	### Inheritance (@extends)
		- groups styles rather than duplicate them
		- placeholders only for extending, don't show up on their own
		- good for fonts, common snippets
		- Careful not to create a ridiculous selector

	### Maps
		- hash
		- @each and map-get (look up in another hash by key)
		- lots of map functions
		- LISTS ARE 1-BASED
		- z-index layers! Map, then @include layer(bottom)
		- entire themes in a map

	### Directives
		#### Functions
			- Different from mixins because functions return a _value_

		#### Conditionals
			- if and else, comparators

		#### Loops
			- Each - e.g. loop through a list, interpolate into base string instead of typing it all out
			- For
			- While

	### Fancy applications
		- rocket demo

## Media Queries
	- can't use @extends in media queries
	- also no auto grouping so careful!

## Modular Architecture
	- Yeah so far I've been kinda breaking things out differently each time. But at least things are broken out. Now I need to define some sort of plan
	- BEM naming conventions
		- .block__element--modifier
		- __ is child
		- -- is variation

		- I would give my elements semantic names, and in Sass extend presentational placeholders into them

	- Augh choice paralysis. Guess I'm just going to have to read all 3 of OOCSS, SMACSS, and Atomic Design and sort of synthesize my own approach

	- Julie used sort of smacss on design.articulate.com
		- base/
			- framework type stuff like element selectors, layout, grid, global vars
		- helpers/
			- mixins, placeholders, utilities (override !important styles that should for sure be applied)
		- modules/
			-all the actual content-focused styles

		-So I guess I haven't been all that far off as far as organization goes.
		-Don't worry about getting it all right immediately. Just keep making things and whenever I encounter a code smell or something that isn't DRY, check out the Sass technique to address that

## Libraries
	- Susy for grids?
	- Checkout Sache.in







## To do on example proj
	-factor out colors
	-factor out other vars

## Make takeaways for me
	- modular color naming
	- interpolation for properties as well as values
	- research OO approaches, like structural, then skin (e.g. button and variations)
	- Define lists of stuff and @each over them with interpolation to generate
	- use csscss to find duplicate styles
	- Sass Style Guide (coding style that is)
	-"No one really knows what they're doing right now, so just write something that doesn't suck."

## Questions
	- mixin or placeholder
		- mixin returns a value, but placeholders grouped selectors
	-Does she have a way to handle code she finds herself reusing all the time, like maybe some custom mixins? Just copy it around? Scaffold?

