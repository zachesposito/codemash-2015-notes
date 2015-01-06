# Security 1 with Jim Manico
# Jan 6 8am

## HTTP Basics
	- don't trust it!!
	- requests and responses
	- stateless
		- Cookies enable server-side session
	- Ads == game over
	- HTTP Verbs
		- GET and POST are most important to us devs
		- POST more secure by far
	- Use HTTPS for everything

**RULE 1: Never put sensitive data in a get request, so leaky**

	- Security response headers
		- HTTP basic authentication is crap
		- Allow cross domain decreases security
		- Strict transport
		- Set cookie -  heart of session management

**RULE 2: We cannot trust any part of the HTTP request**

	- Attackers can totally and easily manipulate all that stuff
	- webgoat -  practice on insecure app
	- Intercepting proxy server
		- intercept your own traffic locally
		- webscarab
	- Tamper Data -  FF plugin
		- intercept handshake -  can mess with data even over HTTPS!

	- GET requests
		- manual url
		- any assets
		- default form submission
		- jquery.get()

		- leaky:
			- bookmarks
			- history
			- proxy server logs
			- web sevrer logs
			- referer headers

		- should be simple, just for basic data retrieval
			- should be nullipotent
			- do not use for anything else

	- POST requests
		- account lockout is a terrible idea -  can hold site hostage!
		- better way to stop brute force: *multi-factor authentication*
		- few different ways to properly do state
			1) request
				- trivial to change
			2) session
				- can just delete cookie header
			3) database
				- track failures here
			- But don't do account lockout

	- HTTPS
		- always. Little more work but really it's just necessary

			1) Confidentiality
			2) Integrity, can't modify
			3) Authenticity, is actually what it claims

			- Also, can be good for SEO

		- StartTLS, etc have free certificates
		- Don't ask for permission just do it
		- Don't be a lazy jerk
		- *Use TLS for everything!*
		- Only submit sensitive data in HTTPS request body

		- Don't leak technical info, just makes it easier to attack

		- Cookies
			- expiration date matters not at all
				- it's just a text file, can do whatever you want to it
			- What really matters is server side session timeouts
			- *Secure flag*
				- only HTTPS
			- *HTTPOnly flag*
				- disable reading via javascript

		- *Response headers to use*
			- X-frame-options
				- anti clickjacking
			- x-xss-protection
				- anti cross site scripting, don't depend entirely on this though
			- x-content-type-options: nosniff
				- stop IE from exposing itself
			- content security policy
				- super good, new
				- Esp for ui work
			- access-control-allow-origin
			- https strict transport securty
				- forces https at browser level for a time (18 wks)
				- chromium can hardcode your domain for https
			- cache-control / pragma
				- use judiciously for sensitive data

		- ASVS from OWASP
			- Application Security Verification Standard
			- Fork it for your company
			- https://github.com/OWASP/ASVS

## Authentication and Session Management
	
	- salted hashes no longer good enough
	- use KDF -  key derivation function
	- multi-factor

	- If your boss tells you to not do this stuff, ignore him. IF you get fired, good because you'll find a better job for more money soon

	- Authorization: is the entity allowed to do X
	- Authentication: logging in, verifying entity identity

	- Authentication sesion
		- area of memory or storage to track stuff about users
		- logged in entities get a session id in a cookie
		- session must timeout
		- session id is usually all that is needed to hijack a session

	- *Doing cookies right*
		- 

	- Don't do encryption yourself, use a library like google keyczar?

	- Authentication workflow
		1) Start HTTPS, deliver login form
			- if you send form via http, you lose integrity!!
		2) Submit credentials (user, pass, multifactor token)
		3) Create session, deliver cookie to user
		4) Do cool stuff
		5) Potential re-authenticaion
			- such places as:
				- change password
				- delete account
				- new address
		6) Logoff or idle session timeout
		7) Absolute session timeout
			- often needs to be done manually
			- remember me cookies are not good without really thinking about how you're doing it
				- maybe you could store the username? Idk there might be a safe way
		8) Invalidate session

	- Authentication Dangers
		- Poor password management
			- stolen DB revealing password data
			- brute force attack
				- many guesses on one account
				- one password on many accounts
			- Simple password policy allowing faster guesses or unlimited guesses
				- *Forbid really common passwords for that region*
				- Zato.com
			- password reuse: attacks on one site affect others

		- Username harvesting
			- registration page can reveal
			- leaked usernames and email addresses via timing attack
				- noticing good user names return error slower than bad name
				- Don't screw with threads, yahoo will laugh at you
			- *Usernames should be private, use separate display name*
			- *Make login errors generic*
			- Twitter screws this up
			- 

		- Weak "forgot password" feature
			- plaintext over email D:
			- reset links over email
			- original passwords over email

		- Session Management Dangers
			- forcing victims to use known session IDs (fixation)
				- disable url rewriting? Don't understand this one
				- Invalidate any existing session on login
			- weak or predictable session IDs
			- hijacking via XSS
				- *counter: HTTPOnly flag*
			- hijacking via network sniffing
				- *counter: Secure flag*

		- Defense
			- Brute force
				- Vertical
					- track total failed logins over time
					- detect spike
					- rate limiting

				- Horizontal
					- MF auth
					- account locking (noooo)
					- obscure user names
					- rate limiting
					- strong password policy

				- *don't indiscriminately block IPs*
					- could be tons of people behind 1 ip, like AOL, China, etc

			- Username harvesting
				- send over https/ssl/tls
				- generic login errors
				- ensure good and bad names take same time to process
				- This doesn't matter if usernames are public or visible in registration
				- Make usernames obscure and assigned instead of chosen

			- Session hijacking
				- Reauthenticate on sensitive actions
				- server-side enforcement of password complexity and strength
				
			- Session Fixation
				- make new session id, invalidate old session
				- disable url session rewriting

			- Logout
				- put logout button in top right corner

		- How to store passwords in DB?
			- never use hash
				- can crack the shit out of it, see $5k comp with video cards
				- salt is same as IV -  init vector
				- use user-specific salt
					- unique to user
			- Use algorithm that's slow on purpose
				- buys you some more time
				- *PBKDF2*
					- not the strongest, but best support
					- make numerical value as _high as you can tolerate_ (login)
				- *bcrypt*
					- max strength, but low support
				- Imposes difficult on attacker AND defender!


			- Basic Password Defense
				- disable all autocomplete
				- Only send passwords over https post body
				- never display password in the browser
					- <input type="password">

				- Offline
					- Avoid hashing or encryption
					- Use proper KDFs 
					- Use random and unique per-user salts
						- deduplicate
					- Strict password policy

				- Online
					- Ban top X commonly used passwords
					- Rate limiting
					- MF auth
					- Behavior Analysis
						- Trojan Combat
						- balance against privacy?
					- Anti-phishing
						- early detection and takedown
						- watch for bad referers on your image requests
						- Blank referer is ok? Can't the attacker control that? Or is that not the case because this request is actually coming from the victim, not the attacker
					- Good network security

			- Password Policy
				- length inversely proportional to needed complexity

			- Attacks on modern password hashes
				- People sometimes specially mint their own hardware optimized just for this

				1) PBKDF
					- pretty good but can be overcome by determined attacker
				2) Bcrypt
					- stronger
				3) scrypt
					- insane strong, deliberately takes up lots of memory
						- above 32mb
					- for like huge banks, nation-level stuff

				- Strength comes at the cost of scalability

			- HMAC
				- good for high-scalability
				- key is in server-side vault
				- super fast, difficulty is only on attacker
				- system relies on key
				- have to back up or _you are screwed_. Your business will fail

			- Proper Forgot Password
				- require identity question
				- ask one or more security question
				- send the user a randomly generated token via out-of-band communication (SMS)
				- twofactorauth.org

			- Federated Identity and SAML
				- XML based, among business
				- Centralized authentication athority
				

			- MF Auth
				- Know
				- Have
				- Are
				- Do

				- Blizzard was first main one

### 3 main things to learn
	- Certificate Pinning
		- hardcoding some certificate details into browser (chrome)
		- see Jeff Walton of OWASP

	- HSTS
		- force browser to always use HTTPS
		- must be delivered over HTTPS
		- must use include subdomains
	
	- Forward Secrecy
		- ephemeral keys in SSL
		- RSA
		- mozilla has good TLS guide related to this


## How to judge where to draw the line between usability and scalability and strength?

## Review
	-Pro
		-super thorough
		-explicit instructions on how to apply

	-Con
		-way too much info for 4 hrs, kinda rushed