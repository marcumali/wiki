# Web Development Wikipedia

[MARCUMALI](https://marcumali.github.io) | [HTML](https://github.com/marcumali/wiki-html) | [CSS](https://github.com/marcumali/wiki-css) | [JAVASCRIPT](https://github.com/marcumali/wiki-javascript) | [WORDPRESS](https://github.com/marcumali/wiki-wordpress) | [PHP](https://github.com/marcumali/wiki-php)

Guide and best practice of web development

## Always

* Test dynamic content longer/shorter/no text/images
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
	add_filter('login_errors', 'wrong_login');
	```
