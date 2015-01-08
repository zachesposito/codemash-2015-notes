# Object Oriented Javascript
Jordan Kasper - @jakerella

- NomadJS - online javascript user group

## OOP
	- objects
		- what it is and what it does

	- abstraction
		- strip away detail to get to essence

	- encapsulation
		- make an interface so don't need to worry about internals

	- inheritance
		- A is a type of B

	- polymorphism
		- an Animal can Run, but Dogs Run differently from Rabbits

	- public, private, privileged

## Is JS not Functional?
	- can be kinda ish
	- but often JS runs in browser, which has state

	- ** really JS is multi-paradigm **

	- Everything in JS is interacted with via/as an object (e.g. primitives)
		- except undefined

	- Functions are just objects

	- Object literals only so useful, hard to reuse
		- really best for data structs

## Constructor
	- Javascript does NOT have classes
		- prototypical

	- this in constructor is the newly created object
	- prototypes have dunderprotos __proto__

	- "new" keyword
		- not instance of class
		- objects with a prototype chain
		- Makes a new empty object, then run the prototype's constructor
		- Some people say don't use new, instead manually call object.create and run a passed prototype
			- to do in old ie need ES5 shim

	- Dunderproto refers to prototype from which object was created
		- don't set it manually

## Member Access Types
	- Public
		- anything on prototype, this or instance

	- private
		- javascript only has 1 scope: function scope
		- var alive = true;

	- priveleged
		- functions declared within functions KEEP the scope from when they were declared
		- This is closures

	- static
		- 

## Inheritance
	- Animal.apply(this, [any, args, to, parent, constructor])
	- ahhhhh prototypes pointing to prototypes
		- Dog.prototype = Object.create(Animal.prototype);
		- Dog.prototype.constructor = Dog;

	- dunderprotos point to parent prototype
	- fallback mechanism
		- that's how all objects have toString even though you didn't set
	- dog.prototype.isPrototypeOf(Animal)

## Interfaces (Mixins)
	- object literal of things any creature with that interface will have
	- e.g. Domesticated {} for dog
	- use a helper method to apply
		- 3rd party library extend method
	- changing the dog prototype adds this to all instances because of the fallback chain
	
## ES6 Classes
	- kinda like class syntax of other language
	- class, contstructor, super
	- but all just syntactic sugar, perhaps best to not use to avoid incorrect assumptions