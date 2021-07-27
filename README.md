#  PHP CS Fixer - Laravel Coding Style Ruleset

This package allows you to use the set of rules for [PHP CS Fixer](https://github.com/FriendsOfPhp/PHP-CS-Fixer) created and recommended by [Laravel Shift](https://laravelshift.com/).

You can find the **original and official** source of the ruleset in [this gist](https://gist.github.com/laravel-shift/cab527923ed2a109dda047b97d53c200).

This ruleset was originally created to work with PHP-CS-Fixer 2.x and has been upgraded to 3.x

## Installation
You can install the ruleset via composer using the following command:

```sh
composer require --dev eduarguz/shift-php-cs
```

This package will also require the `^3.0` version of `friendsofphp/php-cs-fixer` package .

## Usage
This package only gives you easy access to the recommended ruleset. The common and usual PHP-CS-Fixer setup
is still required:

In case you don't have one, create your `.php-cs-fixer.php` file.

```sh
touch .php-cs-fixer.php
```

Put your `Finder` config inside. This will tell PHP-CS-Fixer where to run.

Usually, for a Laravel Project this is the config:

```php
<?php

use PhpCsFixer\Finder;

$project_path = getcwd();
$finder = Finder::create()
    ->in([
        $project_path . '/app',
        $project_path . '/config',
        $project_path . '/database',
        $project_path . '/resources',
        $project_path . '/routes',
        $project_path . '/tests',
    ])
    ->name('*.php')
    ->notName('*.blade.php')
    ->ignoreDotFiles(true)
    ->ignoreVCS(true);

return \ShiftCS\styles($finder);

```

Run your fixer.

```sh
./vendor/bin/php-cs-fixer fix
```

Run on CI

```sh
./vendor/bin/php-cs-fixer fix --dry-run
```

## Upgrade from 1.x to 2.x version of this package (to PHP-CS-Fixer 3.x)

```sh
composer require --dev eduarguz/shift-php-cs
```

Rename any of your existing files:

`.php_cs` -> `.php-cs-fixer.php`

`.php_cs.dist` -> `.php-cs-fixer.dist.php`

`.php_cs.cache` -> `.php-cs-fixer.cache`

## Resources

- Sharing PHP-CS-Fixer rules across projects and teams. [Laravel News Article](https://laravel-news.com/sharing-php-cs-fixer-rules-across-projects-and-teams)
- Laravel Shift Recommended Coding Ruleset. [Gist](https://gist.github.com/laravel-shift/cab527923ed2a109dda047b97d53c200) - [Shift](https://laravelshift.com/)
