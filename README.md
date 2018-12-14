# Frontend wiki

## Always

* Test dynamic content longer/shorter/no text/images
* Comply with Styleguides
* Test components in a different location (e.g. formfields, buttons etc.)
* Hover/Focus-states on interactive items (links/buttons/etc)
* Is it responsive in between mobile/tablet/desktop
* Uncomment code that is needed on live site (e.g. Google Analytics)
* Compare the approved design with the final website (spacing/fonts/colors)
* Third-party items are connected to the proper accounts (if applicable)
* Test on different browsers and platforms (more or less, more when new site)
* Compare end result with design
* Test on screen size points:
	- 320px _(iPhone 2-5)_
	- 375px _(iPhone 6/7)_
	- 414px _(iPhone 6/7 Plus)_
	- 768px _(iPad portrait)_
	- 1024px (_iPad landscape)_
	- 1280px _and up (majority of desktops)_

## New sites/Large updates on existing sites
* One and only one H1 on each page
* Semantically correct use of headings, don’t set heading level based on design
* Appropriate meta data (page title/description/keywords/images/social media sharing)
* Images have alt-attributes
* Favicon
* Tracking is activated (e.g. Google Analytics)
* 404 page exists and is informative/or redirect to index (declared in handover)
* Search page exists and works (if applicable)
* Social-sharing works (if applicable)
* All CMS-editor output is styled (if applicable)
* Only include (bootstrap-)components we use
* Avoid CMS-specific classes

## Continuous improvement (don’t need to be perfect)
* HTML/CSS passes validation
* No broken links
* Correct spelling on content
* Displays & functions correctly in Internet Explorer 9
* Passes WCAG 2.0 level A (or preferably AA)
* Cookie-information
* Is it possible to navigate the site through tabbing?

## General
* don't try to prematurely optimize your code; keep it readable and understandable.
* soft indents, 2 spaces
* save svgs in assets/images and name them according to class name
* follow the current method (Bootstrap, BEM or SMACSS)

## HTML5
* attribute values within double quotes e.g. class="..."
* `<a>` with `target="_blank"` add `rel="noreferrer noopener"`
* Use aria-expanded/aria-controls/aria-hidden
* `<a>` are for links, if you need a button to trigger js only then use `<button>`
* if href is targeting an element(ID) that is not focusable add `tabindex="-1"` to target element

## JavaScript

* when `.on('click', ... )` is used, allow keydown as well
* put listeners on `.js-classes` and toggle either `aria-attributes` (when present) or classes e.g. `.active`
* if a listener needs to address a certain ID or class pass it as an attribute. Exception may occur when using third party plugins.
* use .on('click', ... ) instead of .click() which is an alias for .trigger('click') that can not handle a _second argument. Additionally, what this means is that there's no way to assign a delegate via .click(...)_

## CSS

* try to avoid page specific css since it's not a modular way of working don't nestle more than 2 levels unless:
* `:pseudo. @content-mixins` or media query (then aim keep it under 4)
* mobile first since it prevents CSS reset on mobile
* `.js-classes` (preferably) or `#js-id` for javascript functions connected to the DOM
* Use `http://b64.io/` for svgs and save us from http requests and horrible svg sprites.

## Good selector intent / low specifity in SCSS, avoid

* There are some exceptions to these rules but 98% of the time they should apply.
* IDs e.g. `#my-page`
* Types e.g. `header`
* Descendants e.g. `ul li`
* Selector nestle e.g. `.block ul li a`
* Qualified selectorns e.g. `ul.a`
* Long selectors e.g. `.home .header ul.primary-nav .primary-nav-link`
* Universals

## Syntax

* be specific or generic
* do not use camelCase on selectors, use lower-case and hyphen-delimited syntax
* row break after each selector { and }
* every rule on it's own line
* space after property:
* space between selector and {
* space between selector combinators e.g. `.selector` ~ `.selector`
* include a semicolon at the end of the last declaration in a declaration block.
* use simple quotation for 'strings'
* properties with 0-value should not have a unit e.g. `margin: 0 10px 0 0;`
* include a space after each comma in comma-separated property values e.g. `rgba(0, 0, 0, .5)`
* media queries nestled in class
* hover-state within media-query since there's no reliable way to check for touchscreen
* long, comma-separated property values - such as collections of gradients or shadows can be arranged across multiple lines in an effort to improve readability e.g.
* the order of properties in a selector:
	- `@extend`
	- `@include` without inner `@content`
	- properties, alphabetic order
	- `@include` with inner `@content`
	- nested rule sets
* vendor prefix order:
	- `-moz-`
	- `-webkit-`
	- `no vendor`

## BACKEND

* Set most appropriate image sizes in admin and in output
* Forms are submitting data properly & gives the user feedback
* Admin username is not _admin_
* Database has another prefix than `wp_`
* Comments are disabled (if not used)
* WordFence
* Hide wp-config in htaccess
* Disable theme and plugin editor
* Remove unused themes and plugins
* Don’t allow search engines to find page until (remember to turn it on when going live)
* Remove `wp-config-sample.php`
* config.php
	- `define('DISABLE_WP_CRON', 'true');`
* function.php
	- `add_filter('xmlrpc_enabled', '__return_false');`
	- 
	```php
	function remove_version() { 
		return ''; 
	} 
		add_filter('the_generator', 'remove_version');
	```
	-
	```php
	function wrong_login() { 
		return 'Wrong username or password'; 
	} 
	add_filter('login_errors', 'wrong_login');```
