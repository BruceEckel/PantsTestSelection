# Selecting Alternate File and Function Names for Pytest Using Pants

The Pytest documention introduces the ability to change both the files
searched for tests and the function names that are considered tests.
See here: <https://docs.pytest.org/en/7.1.x/example/pythoncollection.html#changing-naming-conventions>.

This repository demonstrates how to achieve this effect when using Pants.
Following the suggestions [here](https://docs.pytest.org/en/7.1.x/example/pythoncollection.html#customizing-test-collection), we configure Pants to search
all python files for tests. Using the example [here](https://docs.pytest.org/en/7.1.x/example/pythoncollection.html#changing-naming-conventions) we consider a test function to be one with a name ending in `_check`. The parts of the `pytest.ini` file that produce these effects look like this:
```
# `python_files` has no effect on Pants; It's only used by the standalne pytest
# program. Pants allows you to control scope of any verb (goal) via wildcards
# like :: on the command line in an ad-hoc way.
python_files = *.py  # Discover tests in every python file
# Only consider a function to be a test if it ends with '_check' (this IS
# recognized by Pants):
python_functions = *_check
```

