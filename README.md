# Lando config for Drupal 11 plus useful tooling commands/scripts

# How to use

* Git clone this repo.
* Go to https://www.drupal.org/project/drupal/releases/11.x-dev and run the `composer create-project` command shown there to create a Drupal 11 project in a different directory.
* Copy `.lando.yml` and `./lando/` from this repo into the root of the Drupal 11 project directory.
* `cd` into the Drupal 11 project directory.
* Edit `./web/sites/default/settings.php`
  * Uncomment these lines:
  ```
  if (file_exists($app_root . '/' . $site_path . '/settings.local.php')) {
    include $app_root . '/' . $site_path . '/settings.local.php';
  }
  ```
* Run `lando start`.
* Assuming `lando start` completes successfully, visit one of the URLs given.
* Follow the Drupal installation GUI. When asked for database credentials, enter:
  * Database name: drupal
  * Database username: drupal
  * Database password: drupal

# Lando tooling commands

Included are potentially useful tooling commands/scripts. Most of them will not be usable until you require the dependency via Composer. For example, `lando composer require drush/drush`.

Feel free to delete any that are not useful to you.

Run `lando` to see all commands.

## lando drupal-reinstall
```
lando drupal-reinstall
```
DROPs the current database, runs `composer install`, `drush site:install`, runs database updates, runs composer install and clears caches.

## lando drupal-reset
```
lando drupal-reset
```
KEEPs the current database, runs `composer install`, runs database updates, runs composer install and clears caches.

## lando drupal-create-users
```
lando drupal-create-users
```
Creates Drupal test users. You will need to modify `./lando/scripts/drupal-create-users.sh` for your project.

## lando logs-drupal
```
lando logs-drupal
```
Tails Drupal watchdog logs.

## lando logs-php
```
lando logs-php
```
Tails PHP error logs.

## PHPCS
```
lando php-cs
```
Runs PHPCS and PHPCBF.

You will need to configure and require PHPCS and dependencies first.

## Twig CS Fixer
```
lando twig-cs
```
Runs Twig CS Fixer.

You will need to run `lando composer require --dev vincentlanglet/twig-cs-fixer` first.

## Behat
```
lando behat
```
Runs Behat tests.

You will need to configure and require Behat and dependencies first.

## Xdebug
```
lando xdebug
```
Toggles Xdebug on/off.

You will also need to configure your IDE.