# Pinax Stripe

[![](http://slack.pinaxproject.com/badge.svg)](http://slack.pinaxproject.com/)
[![](https://img.shields.io/travis/pinax/pinax-stripe.svg)](https://travis-ci.org/pinax/pinax-stripe)
[![](https://img.shields.io/coveralls/pinax/pinax-stripe.svg)](https://coveralls.io/r/pinax/pinax-stripe)
[![](https://img.shields.io/pypi/dm/pinax-stripe.svg)](https://pypi.python.org/pypi/pinax-stripe/)
[![](https://img.shields.io/pypi/v/pinax-stripe.svg)](https://pypi.python.org/pypi/pinax-stripe/)
[![](https://img.shields.io/badge/license-MIT-blue.svg)](https://pypi.python.org/pypi/pinax-stripe/)
[![](https://readthedocs.org/projects/pinax-stripe/badge/?version=latest)](http://pinax-stripe.readthedocs.org/en/latest/?badge=latest)

This app was formerly called `django-stripe-payments` and has been renamed to
avoid namespace collisions and to have more consistency with Pinax.

## Pinax

Pinax is an open-source platform built on the Django Web Framework. It is an ecosystem of reusable Django apps, themes, and starter project templates.
This collection can be found at http://pinaxproject.com.

This app was developed as part of the Pinax ecosystem but is just a Django app and can be used independently of other Pinax apps.


## pinax-stripe

`pinax-stripe` is a payments Django app for Stripe.

This app allows you to process one off charges as well as signup users for
recurring subscriptions managed by Stripe.

Some suggested integration steps:
  1. Overload the templates provided to use your inheritance tree (for bases etc) and block names.
  2. Point your stripe account at the webhook address in the payments urls.
  3. Add the static media snippet from here (or else nothing will actually talk to stripe):
    * http://django-stripe-payments.readthedocs.org/en/latest/installation.html#configuration-modifications-to-settings-py
  4. Set up SSL if you have not already.
  5. Define some plans (see docs).
  6. Run syncdb to generate the necessary tables, then init_plans and init_customers.


## Development

`pinax-stripe` supports a variety of Python and Django versions. It's best if you test each one of these before committing. Our [Travis CI Integration](https://travis-ci.org/pinax/pinax-stripe) will test these when you push but knowing before you commit prevents from having to do a lot of extra commits to get the build to pass.

### Environment Setup

In order to easily test on all these Pythons and run the exact same thing that Travis CI will execute you'll want to setup [pyenv](https://github.com/yyuu/pyenv) and install the Python versions outlined in [tox.ini](tox.ini).

If you are on the Mac, it's recommended you use [brew](http://brew.sh/). After installing `brew` run:

```
$ brew install pyenv pyenv-virtualenv pyenv-virtualenvwrapper
```

Then:

```
$ CFLAGS="-I$(xcrun --show-sdk-path)/usr/include -I$(brew --prefix openssl)/include" \
LDFLAGS="-L$(brew --prefix openssl)/lib" \
pyenv install 2.7.10 3.2.6 3.3.6 3.4.3 3.5.0

$ pyenv virtualenv 2.7.10 test-2.7.10
$ pyenv virtualenv 3.2.6 test-3.2.6
$ pyenv virtualenv 3.3.6 test-3.3.6
$ pyenv virtualenv 3.4.3 test-3.4.3
$ pyenv virtualenv 3.5.0 test-3.5.0
$ pyenv global 2.7.10 test-2.7.10 test-3.2.6 test-3.2.6 test-3.3.6 test-3.4.3 test-3.5.0

$ pip install detox
```

To run test suite:

Make sure you are not inside a `virtualenv` and then:

```
$ detox
```

This will execute the testing matrix in parallel as defined in the `tox.ini`.


## Documentation

The pinax-stripe documentation is available at  http://pinax-stripe.readthedocs.org/en/latest/.
The Pinax documentation is available at http://pinaxproject.com/pinax/.


## Code of Conduct

In order to foster a kind, inclusive, and harassment-free community, the Pinax Project has a code of conduct, which can be found here http://pinaxproject.com/pinax/code_of_conduct/.


## Pinax Project Blog and Twitter

For updates and news regarding the Pinax Project, please follow us on Twitter at @pinaxproject and check out our blog http://blog.pinaxproject.com.
