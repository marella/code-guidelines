### Table of contents
- [Development](#development)
- [Coding](#coding)
- [PHP](#php)
- [MySQL](#mysql)
- [HTML](#html)
- [CSS](#css)
- [JS](#js)
- [Icons](#icons)

### Development
- Divide large applications into smaller independent components
- Each component should do one thing and do it well ([Microservices](https://en.wikipedia.org/wiki/Microservices))
- Do NOT mix UI and backend code ([MVC](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller))
- Keep separate copies for development, testing and production
- Use git for version control
- See https://sethrobertson.github.io/GitBestPractices/

### Coding
- Use tabs for indentation (different projects have different conventions but we use tabs)
- Trim trailing white space
- Add new line at end of files
- Split long lines
- Split large files (more files are better for collaboration and version control)
- Use descriptive names for variables and functions
- Avoid global variables
- Use [Sublime Text](http://www.sublimetext.com/) with these settings

```json
{
	"detect_indentation": false,
	"ensure_newline_at_eof_on_save": true,
	"font_size": 14.0,
	"ignored_packages":
	[
		"Vintage"
	],
	"open_files_in_new_window": false,
	"scroll_past_end": true,
	"shift_tab_unindent": true,
	"tab_size": 4,
	"translate_tabs_to_spaces": false,
	"trim_trailing_white_space_on_save": true,
	"word_wrap": false
}
```

### PHP
- One class per file
- Always use namespaces
- Class filenames should be same as class name (case-sensitive) and should be loaded using autoloading functions
- Other filenames should be in lowercase
- In a file either declare symbols (classes, functions, constants, etc.) or cause side-effects (e.g. generate output, change .ini settings, etc.) but do NOT do both
- Do NOT put closing PHP tag `?>` at the end of file
- Turn on all errors and notices during development
- Avoid static methods
- Follow [functional programming](https://en.wikipedia.org/wiki/Functional_programming) whenever possible
- See [PSR-1](http://www.php-fig.org/psr/psr-1/) and [PSR-2](http://www.php-fig.org/psr/psr-2/) standards

```php
<?php
namespace Vendor\Package;

use FooInterface;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class Foo extends Bar implements FooInterface
{
	public function sampleFunction($a, $b = null)
	{
		if ($a === $b) {
			bar();
		} elseif ($a > $b) {
			$foo->bar($arg1);
		} else {
			BazClass::bar($arg2, $arg3);
		}
	}

	final public static function bar()
	{
		// method body
	}
}
```

### MySQL
- Use `PDO`
- Add primary key to all tables
- Use `LIMIT` in all statements whenever possible
- Use descriptive names for tables and columns
- Prefix table names with app name whenever possible
- Avoid database names in statements to make it more portable
- Cache results in memory (Redis) as DB operations are slow
- Put database schema under version control

```sql
SELECT id FROM users WHERE email = ? LIMIT 1
UPDATE users SET status = :status WHERE id = :id LIMIT 1
```

### HTML
- Place all styles at top in head and scripts at the end of body
- Do NOT use inline styles or scripts
- Avoid generating HTML in JS
- Avoid IDs and use only classes for styling
- Combine, minify and optimize assets
- See http://codeguide.co/#html

```html
<!doctype html>
<html>
	<head>
		<meta charset="utf-8">
		<meta http-equiv="x-ua-compatible" content="ie=edge">
		<meta name="viewport" content="width=device-width, initial-scale=1">
		<title></title>
		<link rel="stylesheet" href="css/app.min.css">
	</head>
	<body>

		<!-- content -->

		<script src="js/app.min.js"></script>
	</body>
</html>
```

### CSS
- Do NOT use `@import`
- Reduce specificity
- Avoid using ID or tag selectors
- Classes should be lowercase
- Use hyphens and do NOT use underscores or camelCases in class names
- Bootstrap like naming convention
- Use Bootstrap whenever possible
- See http://codeguide.co/#css

```css
.table {
	margin-bottom: 15px;
}

.card {
	padding: 20px;
}

.card-title {
	font-size: 18px;
}

.card-primary {
	background-color: #abcdef;
}
```

### JS
- Use camelCase for variable and function names
- Cache jQuery lookups `var $this = $(this);`
- Use jQuery whenever possible
- See https://github.com/airbnb/javascript/tree/master/es5

```js
!function(global) {
	'use strict';

	var previousFancyInput = global.FancyInput;

	function FancyInput(options) {
		this.options = options || {};
	}

	FancyInput.noConflict = function noConflict() {
		global.FancyInput = previousFancyInput;
		return FancyInput;
	};

	global.FancyInput = FancyInput;
}(this);
```

### Icons
- Use icon font
- See https://icomoon.io/app/
