# Selecting Alternate File and Function Names for Pytest Using Pants

The Pytest documention introduces the ability to change both the files searched
for tests and the function names that are considered tests. The Pytest default
is to only look for tests inside `test_*.py` or `*_test.py` files, and to look for function names prefixed with `test` inside those files. (Pytest also looks
for class names prefixed with `Test` but we will not cover those here).

This repository demonstrates how to choose alternate Pytest file and function
names when using Pants. Following the suggestions
[here](https://docs.pytest.org/en/7.1.x/example/pythoncollection.html#customizing-test-collection),
we configure Pants to search all python files for tests. Using the example
[here](https://docs.pytest.org/en/7.1.x/example/pythoncollection.html#changing-naming-conventions)
we consider a test function to be one with a name ending in `_check`. The parts
of the `pytest.ini` file that produce these effects *for Pytest* look like this:
```
# `python_files` has no effect on Pants; It's only used by the standalone pytest
# program. Pants allows you to control scope of any verb (goal) via wildcards
# like :: on the command line in an ad-hoc way.
python_files = *.py  # Discover tests in every python file
# Only consider a function to be a test if it ends with '_check'
# (python_functions IS used by Pants):
python_functions = *_check
```

Some Pytest configurations are used by Pants and others are ignored and
controlled by Pants' own configurations (another example: `collect_ignore` in
`conftest.py` is also ignored by Pants). When changing file and function name
discovery you must know what these are and control them through Pants
configurations.

There are two different test setups in this repository. To see the successful
examples, move to the `succeed` directory and run both `pytest` and `./Pants
test ::`. To see the failing examples, move to the `fail` directory and run the
same commands. Look at the `pytest.ini`, `pants.toml` and `BUILD` files in each
subdirectory to see what produces these effects. There are also `README` files
which explain the issues.
