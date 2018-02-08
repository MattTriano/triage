.. highlight:: shell

============
Contributing
============

Contributions are welcome, and they are greatly appreciated! Every
little bit helps, and credit will always be given.

You can contribute in many ways:

Types of Contributions
----------------------

Report Bugs
~~~~~~~~~~~

Report bugs at https://github.com/dssg/triage/issues.

If you are reporting a bug, please include:

* Your operating system name and version.
* Any details about your local setup that might be helpful in troubleshooting.
* Detailed steps to reproduce the bug.


Write Documentation
~~~~~~~~~~~~~~~~~~~

Triage could always use more documentation, whether as part of the
official Triage docs, in docstrings, or even on the web in blog posts,
articles, and such.

Submit Feedback
~~~~~~~~~~~~~~~

The best way to send feedback is to file an issue at https://github.com/dssg/triage/issues.

If you are proposing a feature:

* Explain in detail how it would work.
* Keep the scope as narrow as possible, to make it easier to implement.

Get Started!
------------

Ready to contribute? Here's how to set up `triage` for local development.

1. Fork the `triage` repo on GitHub.
2. Clone your fork locally::

    $ git clone git@github.com:your_name_here/triage.git

3. Install your local copy into a virtualenv. Assuming you have virtualenvwrapper installed, this is how you set up your fork for local development::

    $ mkvirtualenv triage
    $ cd triage/
    $ python setup.py develop

4. Create a branch for local development::

    $ git checkout -b name-of-your-bugfix-or-feature

   Now you can make your changes locally.

5. When you're done making changes, check that your changes pass flake8 and the tests, including testing other Python versions with tox::

    $ flake8 triage tests
    $ python setup.py test or py.test
    $ tox

   To get flake8 and tox, just pip install them into your virtualenv.

6. Commit your changes and push your branch to GitHub::

    $ git add .
    $ git commit -m "Your detailed description of your changes."
    $ git push origin name-of-your-bugfix-or-feature

7. Submit a pull request through the GitHub website.

Pull Request Guidelines
-----------------------

Pull requests should have the following things:

.. _src/triage/component/architect: src/triage/component/architect
.. _src/tests/architect_tests: src/tests/architect_tests
.. _experiment validation: src/triage/experiments/validate.py
.. _example experiment config: example_experiment_config.yaml
.. _experiment module base: src/triage/experiments/__init__.py
.. _experiment algorithm doc: docs/sources/experiments/algorithm.md

- Unit tests. If the code is in a component, say Architect, 'src/triage/component/{component_name}' (e.g. `src/triage/component/architect`_), the tests are in 'src/tests/{component_name}_tests/' (e.g. `src/tests/architect_tests`_). See other tests in that directory for examples on how to write tests, especially those involving database access and fake data.

- If the code adds or changes experiment configuration values:

  - The `experiment validation`_  class should be updated. A best effort should be made to raise any issues with the experiment definition that can be caught before running the full experiment. This can involve checking values against whitelists, inspecting given database tables, or even running some version of given queries through an EXPLAIN command.
  - The `example_experiment_config`_ should be updated with the new or changed experiment configuration, and instructions for using it.
  - If the change breaks old experiment definitions, the experiment config version should be updated in both the `example experiment config`_ and `experiment module base`_

- Documentation. To be more specific:

  - Functions should have docstrings
  - If a change adds or changes functionality for the Experiment, the `experiment algorithm doc`_ should be updated.

- The pull request should work for Python 3.6.

