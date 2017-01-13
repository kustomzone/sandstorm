# Code dependencies

Many web apps need access to libraries via language-specific package
managers like `pip`, `npm`, and so on.

## Supported by the platform stack

If you are using a "platform stack" that has built-in support for
downloading dependencies, like the Meteor stack or the Python stack,
then you can expect `vagrant-spk` to handle downloading and installing
these dependencies for you. Specifically:

* The `uwsgi` stack creates a virtualenv in the `env` directory within
the app's code directory (`/opt/app/env` inside Vagrant) and, if a
`requirements.txt` is present, does `pip install -r requirements.txt'
into the virtualenv.

* The `meteor` stack uses the `meteor build` process to create a
Meteor bundle.

* The `lemp` (PHP) stack looks for `composer.json` in the app
directory and, if present, downloads and runs `composer.phar`
to download the dependencies listed in `composer.json`.

## Beyond the platform stack

If you need to install extra Debian packages, such as PHP extensions
or headers like `libxml2-dev`, you can add commands to [your package's
build.sh](customizing.md#buildsh).

If you are creating your own platform stack, based on the DIY stack,
you will likely also need to customize `build.sh`.
