# Clean Code for Humans
Cory House @housecor
- he has notes available too: http://www.bitnative.com/presentations/handouts/

- fundamentals
- always better to show instead of tell
- "there is no problem so simple that a bad dev cannot make it complicated"
- value of reviewing vocabulary around basics
	- you may know what to do but not know how to explain
- ** Vocabulary for Code Quality **

## Reasons to Care
	1) Debugging is twice as hard as writing
	2) It's your job to manage complexity
	3) Technical debt is depressing T_T
	4) No time to be sloppy, will always pay for it later
	5) You're lazy
	6) Don't be a verb
	7) If you are an expert you can talk about it

	- Fast + clean is attainable

## 
	1) Right tool for the job
		- avoid black and white maxims, it always depends on context
		- one language per file, no overlaps
		- every tech is potential eeeeeeeviil

	2) Maximizing signal to noise ratio
		- TED:
			- Terse
			- Expressive
			- Do one thing
		- goal: density. More in each "eyeful"
		- Important because:
			- our brain is the compiler
			- the mess builds quietly

	3) Self-documenting code
		- Understanding original programmer's intent is often the hardest thing (1979)

## 
	1) Naming
		- clearly and semantically name stuff
		- if need help, talk to a duck or something
		- WARNING SIGNS: and/if/or
		- Methods should have no side effects
		- Avoid abbreviations
			- it's not the 70's, we're don't have character limits
			- converting in your head is extra work
			- Easier to talk about code when things are pronouncable
		- code should read like an outline
			- high- and low-level methods
		- methods should be really tiny

	2) Comments
		- stinky!
		- usually instead of writing a comment, you could have written clear code
		- if code gets refactored, comments probably don't get updated
		- Good for broad summaries, or things that aren't expressible in code like links to external docs
		- replace comments with enums
			- just like Sass

		- Zombie code
			- not quite dead, not quite alive, haunts you
			- commented out code blocks
			- KILL IT

			- reduces readability
			- creates ambiguity - intentional or not?? why half-remove?
			- hinders refactoring
			- adds noise to searches
			- code isn't "lost" if you're using source control, and if you're not you're a moron

		- Don't litter - comments from 2002 - belongs in source control

	3) Conditionals
		- turn if {} else {} into ternary operator
			- don't nest though

		- Compare booleans implicity
			- if (loggedIn) instead of if (loggedIn == true)
			- bool goingToChipotleForLunch = cashInWallet > 6.00;

		- Don't not be anti-negative
			- if (loggedIn) instead of if (!isNotLoggedIn)
			- Speak in the positive whenever you can, in general!

		- Avoid "stringly" typed
			- if (employeeType == "manager")
			- should be if (employee.Type == EmployeeType.Manager)
			- let the computer do this work for you

	4) Functions
		- brain tracks about 7 things at once
		- comprehension decreases beyond 3 levels of nested ifs (1986)
			- similar to Sass in that it's a sign you need to refactor

		- extracting is like footnotes

		- Fail fast (early)
			- throw exception as soon as possible
			- don't just log error then move on

		- Refactor try {} contents to its own method
		- Return early - don't process extra stuff
		- Mayfly variables - init as close to first use as possible
		- _Do ONE THING_

## Deep thoughts
	- ever complained that a method is too short or a class too small?
		- much less likely than doing way the hell too much

## The Path Forward
	- No broken windows in your code
	- Leave the campground better than you found it
	- 




## takeaways
	- really ought to speak
