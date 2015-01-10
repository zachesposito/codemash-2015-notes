# Accessibility with (WAI-)ARIA
Dylan Barrell
Deque

- $8 trillion
	- estimated disposible income for families with a person with a disability
- 15% of people have some kind of relevant disability
- More than just screen readers
	- e.g. amputees, deaf
	
- Guiness - all about the POUR
	- perceivable et al

- Role
- Name
- State(s)
- Value

- just like modular sass considerations

- ARIA is about semantics?

- Can specify a focus order 

- Provide feedback for node x of y, async content

- accessibility, RWD, progressive enhancement, modularity are all connected

## 3 Trees to Consider
	- DOM
		- what you already know
	- Accessibility tree
		- from dom > browser > OS > assistive device
	- Composed tree (web components)

- ARIA has roles AND attributes

- Native semantic elements work fine, don't do <a role="button"> when you can use <button>

- if you can't get out of bad semantics, role="presentation"

- iOS autozoom can affect gesture resolution


## questions
	- versions of aria spec? Do we need to consider multiple conflicting versions?
		- 
	- element with role should have the event handler
		- how does this affect delegation?

## takeaways
	- I'm still really not sure what this is
	- do I just add the roles and bam I get extra functionality? Or only in weird assistive devices?
	- How is this different from just writing good, semantic html and progressively enhanced css?
	- I guess I should get a hold of a screen reader or something and start solving problems with it, then I would probably see the value of this
	- I guess I need to read more 