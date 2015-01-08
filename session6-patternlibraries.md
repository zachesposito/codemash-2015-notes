# Fostering Collaboration with Pattern Libraries
Bermon Painter
Cardinal Solutions

- Sass, Compass, Susy, and Middleman

## Challenge
	- Consistency that is easy to maintain

## Case Study
	- tons of developers, multiple teams, one application
	- No FE devs or ux people, made a mess
	- Slow because they weren't minifying, concat, had lots of http requests, no caching
	- Poor communication across teams - lots of duplicated work
	- Shipped the wrong thing - didn't talk to customers/clients
	- super expensive

## Enter Pattern Library
	- BP differentiates style guide from pattern library like so:
		- style guide = branding data like colors, fonts
		- pattern library = reusable modules
	- Creates consistent UX, aesthetic, language
	- Reusability
	- Maintainability
	- All the stuff I already identified

	### Recognizing Patterns
		- Design systems, not pages (brad frost)
		- e.g. Meetup.com

	### Module requirements
		1) can be nested, no problem
		2) can be combined
		3) must clearfix
		4) responsive
		5) ** separate structural styles from theme styles **
			- or at least, separate default from variations/states
		6) accessible

	### Drawback
		- takes a lot of time up front, both the create, test, and document but also education of others

	### Tech used
		- Middleman
			- Sinatra SSG
		- Sass with Compass
		- Suzy - unobtrusive grid system

	### Pattern Library Content
		1) Code standards
		2) Base elements - BP starts with normalize and customizes, split apart for each version
		3) Modules
			4) Scaffold (structure)
			5) Theme

	### 2 main types
		- static HTML
			- straightforward but hard to keep up with

		- generator
			- hologram like dss, 

		#### Pattern api - holy grail?
			- .slim -> .html
			- . sass -> .css
			- tests + .coffee -> .js
			- ** lonely pattern HAS DONE THIS **
				- they have VERSIONS of patterns
				- holy shit
				- this is really the most important idea I've come across so far here
					- talk to BP or lonely planet about this


## Questions
	- I really hope this company makes this public, would be great to show
	- how do updates


## Takeaways
	- BP uses slim for html?
	- I think I like the format of BP's client PL with standards, base, modules
	- PATTERN APIs WITH VERSIONS
		- make a custom ui component layer
		- but then how to share across projects?
	- order css by structure/scaffold/layout, then theme
		- Like filling in a wireframe?
	- Interpolation for BEM with sass