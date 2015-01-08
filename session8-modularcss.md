# Decoupling the Front-End through Modular CSS
Julie Cameron


- top-down overlyspecific tightly coupled css is not scalable or maintainable
- stop using css selectors for non-css
	- use data attributes

## Modularize CSS
	- modularity is so powerful
	- goal: get to a point where you can make new pages without writing ANY new css
	- predictability - modules are context-independent
	- maintainability
		- decrease complexity and technical debt
	- scalable
		- fearlessly add new stuff
	- DRY - part of the above
	- organized - things have a place

## Methodologies
	### OOCSS
		- Nicole Sullivan
		- Media object - content block containing a fixed-size media element along with other variable sized content like text
			- TT.com TP section
		- Objects
			- abstraction of repetition
			- result: modules with variations

			- object - .media
			- child objects - .media__img
			- modifiers - .media--inline, .media__img--right
			- states - .media--collapsed

	### Best practices
		- Single responsibility
		- use classes for everything, no ids and no base element selectors
		- naming conventions (BEM) .block__element--modifier
		- semantic naming for classes, presentational naming for placeholders/vars
		- separate structure from skin
			- what makes a button look like a button?
				- to identify, apply class to various elements (button example)
			- what makes various button look different?
			-
		- separate container from content
			- objects should look the same no matter where you put them
			- instead of .footer h2, .sidebar h3 {}, make .sectionHeader

	- Forces you to think hard about what's common and break it out

	- Trying to strike a balance between maintenance, performance, and readability

	### SMACSS
		- categorizes objects
			- base
				- default element look
			- layout
				- page sections, grids
			- modules
				- bulk, reusable parts and subclasses (variations)
			- state
				- indicate js dependencies (.is-visible)
				- if SUPER specific then keep with module
			- theme
				- multiple holistic themes, if you have
	
	### Atomic Design
		- assembling
			- atoms
				- element selectors like base above
			- molecules
				- groups of atoms together
				- ui pieces like a search box
			- organisms
				- groups of molecules like .footer, .sidebar

## Going forward
	- Find right level of granularity
	- establish conventions (BEM, categorization, code standards)
	-  


## Takeaways
	- The methodology parts are super useful, but the examples less so because they're just straight CSS, which suffers from not having that extra layer that solves a lot of basic problems
	- Except for things like lists, no more context-dependent element selectors for me
		- make _everything_ an object

