<p align="center"><img src="https://laravel.com/assets/img/components/logo-dusk.svg"></p>

<p align="center">
<a href="https://travis-ci.org/laravel/dusk"><img src="https://travis-ci.org/laravel/dusk.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/dusk"><img src="https://poser.pugx.org/laravel/dusk/d/total.svg" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/dusk"><img src="https://poser.pugx.org/laravel/dusk/v/stable.svg" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/dusk"><img src="https://poser.pugx.org/laravel/dusk/license.svg" alt="License"></a>
</p>

## Introduction

Laravel Dusk provides an expressive, easy-to-use browser automation and testing API. By default, Dusk does not require you to install JDK or Selenium on your machine. Instead, Dusk uses a standalone Chromedriver. However, you are free to utilize any other Selenium driver you wish.

## Official Documentation

This is an alpha release of Dusk. Documentation is in progress.

#### Quickstart (For Laravel 5.4)

> **Note:** Dusk is not currently compatible with Windows. We need assistance from Windows users to provide the code to correctly start Chromedriver on Windows.

    composer require laravel/dusk

Once Dusk is installed, add the `Laravel\Dusk\DuskServiceProvider` to your `config/app.php` configuration file:

    php artisan dusk:install

A `Browser` directory will be created within your `tests` directory containing an example test. Examples of advanced testing and page objects will be available with the full documentation.

To run your tests, use the `dusk` command. The `dusk` command accepts any argument that is also accepted by the `phpunit` command:

    php artisan dusk

#### Environments

To force Dusk to use its own environment file, create a `.env.dusk.{environment}` file in the root of your project. For example, if you will be initiating the `dusk` command from your `local` environment, you should create a `.env.dusk.local` file.

#### Multiple Browsers

If you would like to test a scenario that requires multiple browser windows, such as event broadcasting, simply "ask" for a second browser in your callback signature:

    $this->browse(function ($first, $second) {
        $first->loginAs(User::find(1))
                ->visit('/home')
                ->waitForText('Message');

        $second->loginAs(User::find(2))
                ->visit('/home')
                ->waitForText('Message')
                ->type('message', 'Hey Taylor')
                ->press('Send');

        $first->waitForText('Hey Taylor')
               ->assertSee('Jeffrey Way');
    });

## License

Laravel Dusk is open-sourced software licensed under the [MIT license](http://opensource.org/licenses/MIT)
