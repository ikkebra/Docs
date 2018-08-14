# Installation

---

We assume:

- you have a working [installation of Laravel 5.6](https://laravel.com/docs/5.6#installing-laravel) (an existing project is fine, you don't need a *fresh* Laravel install);

- you have composer registered as a global command & you can run the ```composer``` command from any directory (otherwise, if you need to run ```php composer.phar``` or reference another directory, please remember to adapt the commands below to your configuration);

## Steps

1) In your project's main directory, install CRUD using composer:

``` bash
composer require backpack/crud
```

2) Now run the installation commands for each of the core packages (Base has also been installed, as a dependency):

``` bash
php artisan backpack:base:install
php artisan backpack:crud:install
```

Note: If you'd also like to enable the [file manager functionality](https://backpackforlaravel.com/uploads/home_slider/4.png), reply "yes" when the installer asks you. By default it lets users manage the ```public/uploads``` directory, but you can change that in the ```elfinder.php``` config file.


3) [Optional] You can now:
- Change configuration values in ```config/backpack/base.php``` to make the admin panel your own. Backpack is white label, so you can change everything: menu color, project name, developer name etc.
- If your application has only one login screen (for the admins), that means you're not going to use the auth controllers that Laravel provided by default. You're only going to use Backpack's auth controllers. You can keep the Laravel ones in your project, of course. But some people like to delete them to not get confused later on:   

``` bash
# OPTIONAL! Please read the notice above.
rm -rf app/Http/Controllers/Auth #deletes laravel's demo auth controllers
```

That's it. If you already know how to use Backpack, next up you'll probably want to [create CRUD Panels](/docs/{{version}}/introduction#creating-crud-panels).

> If it's your first time installing Backpack, it is **highly recommended** that you go through our [Getting Started series](/docs/{{version}}/getting-started-basics), to understand how Backpack works. That's why we created it - to help you learn how to use this admin panel framework. In ~23 minutes we'll teach you 80% of what you can do, and how.

## Extensions

In case you want to add extra functionality that's already been built, check out [the installation steps for the extensions we've developed](/docs/{{version}}/install-optionals).


## Frequently Asked Questions

- **Error: The process X exceeded the timeout of 60 seconds.** It might mean Github or Packagist is unavailable at the moment. This usually doesn't last for more than a few minutes, so you can run ```php artisan backpack:base:install --timeout=600``` to increase the timeout to 10 minutes. If this doesn't work either, take a look behind the scenes with ```php artisan backpack:base:install --timeout=600 --debug```, and refer to [this thread](https://github.com/Laravel-Backpack/Base/issues/217).

- **Error: SQLSTATE[42000]: Syntax error or access violation: 1071 Specified key was too long**. Your MySQL version might be a bit old. Please [apply this quick fix](https://laravel-news.com/laravel-5-4-key-too-long-error), then run ```php artisan migrate:fresh```.

- **Any other installation error?** If you can't install Backpack\\Base because of a different error, you can [try the manual installation process](https://laravel-backpack.readme.io/docs/frequently-asked-questions#section-how-do-i-manually-install-base), which you can tweak to your needs.