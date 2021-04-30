# Quickstart in 5 minutes

Getting started with X is easy!
Here's a quick tutorial to get you up and running in 5 minutes or less.
Start your timer and here we go!

## Code

In order to first start using X, let's start with an entirely empty project directory.
This shouldn't be too confusing, but here's how you can do so on the common line:

```bash
$ mkdir ~/projects/acme
$ cd ~/projects/acme
```

Next, we can start by taking a look at a simple example application.
You can use this example to get started by creating a new `app.php` file in your empty project directory:

```php
<?php

require __DIR__ . '/vendor/autoload.php';

$loop = React\EventLoop\Factory::create();
$app = new Frugal\App($loop);

$app->get('/', function () {
    return new React\Http\Message\Response(
        200,
        [],
        "Hello wörld!\n"
    );
});

$app->run();
$loop->run();
```

On a code level, this is everything you need to get started.
For more sophisticated projects, you may want to make sure to [structure your controllers](../best-practices/controllers.md),
but the above should be just fine for starters.

## Installation

Next, we need to install X and its dependencies to actually run this project.

> ⚠️ **Beta**
>
> This project is currently in closed beta, so the installation requires a manual step first.
> This will not be necessary once the project is released to the public.
>
> Start by creating a new `composer.json` in the project directory with the following contents:
> 
> ```json
> {
>     "repositories": [
>         {
>             "type": "vcs",
>             "url": "https://github.com/clue-engineering/frugal"
>         }
>     ]
> }
> ```

Thanks to [Composer](https://getcomposer.org/), this installation only requires a single command.

> ℹ️ **New to Composer?**
>
> If you haven't heard about Composer before, Composer is *the* package manager for PHP-based projects.
> You can think of it as what NPM is to JavaScript, *but better*.
> If you haven't used it before, you have to install a recent PHP version and Composer before you can proceed.
> On Ubuntu- or Debian-based systems, this would be as simple as this:
>
> ```bash
> $ sudo apt install php-cli php-mbstring php-xml composer
> ```

In your project directory, simply run the following command:

```bash
$ composer require clue/frugal:dev-main
```

This isn't NPM, so this should only take a moment or two.

## Running

The next step after installing all dependencies is now serve this web application.
One of the nice properties of this project is that is *runs anywhere* (provided you have PHP installed of course).

For example, you can run the above example using PHP's built-in webserver for
testing purposes like this:

```bash
$ php -S 0.0.0.0:8080 app.php
```

You can now use your favorite webbrowser or command line tool to check your web
application responds as expected:

```bash
$ curl -v http://localhost:8080/
HTTP/1.1 200 OK
…

Hello wörld!
```

And that's it already, you can now stop your timer.
If you've made it this far, you should have an understanding why X is so exciting.
As a next step, we would recommend checking out the [best practices](../../best-practices/) in order to deploy this to production.

Happy hacking!