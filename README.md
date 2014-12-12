test_sugardough
==========

[![Build Status](https://travis-ci.org/mozilla/test_sugardough.svg?branch=master)](https://travis-ci.org/mozilla/test_sugardough)

[![Coverage status](https://coveralls.io/repos/mozilla/test_sugardough/badge.svg?branch=master)](https://coveralls.io/r/mozilla/test_sugardough)

Run the tests
-------------

There's a sample test in `test_sugardough/base/tests.py` for your convenience, that
you can run using the following command:

    pip install coverage
    coverage run manage.py test

This is also the command used by [tox](https://testrun.org/tox/latest/), that
you can install and run yourself (it'll run the exact same thing that is run by
[travis](https://travis-ci.org)):

    pip install tox
    tox

The `.travis.yml` file will also run [coveralls](https://coveralls.io) by
default.

If you want to benefit from Travis and Coveralls, you will need to activate
them both for your project.

Oh, and you might want to change the "Build Status" and "Coverage Status" links
at the top of this file to point to your own travis and coveralls accounts.


Docker for development
----------------------

0. Make sure you have [docker](https://docker.io) and [fig](https://pypi.python.org/pypi/fig)
1. fig up

Note that this will probably not work with
[boot2docker](https://github.com/boot2docker/boot2docker), as the
volumes will not get mounted.


Docker for deploying to production
-----------------------------------

1. Add your project in [Docker Registry](https://registry.hub.docker.com/) as [Automated Build](http://docs.docker.com/docker-hub/builds/)
2. Prepare a 'env' file with all the variables needed by dev, stage or production.
3. Run the image:

    docker run --env-file env -p 80:80 mozilla/test_sugardough
