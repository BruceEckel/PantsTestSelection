# Selecting Alternate File and Function Names for Pytest Using Pants

The Pytest documention introduces the ability to change both the files
searched for tests and the function names that are considered tests.
See here: <https://docs.pytest.org/en/7.1.x/example/pythoncollection.html#changing-naming-conventions>.

This repository demonstrates how to achieve this effect when using Pants.
Following the suggestions [here](https://docs.pytest.org/en/7.1.x/example/pythoncollection.html#customizing-test-collection), we configure Pants to search
all python files for tests. Using the example [here](https://docs.pytest.org/en/7.1.x/example/pythoncollection.html#changing-naming-conventions) we consider a test function to be one with a name ending in `_check`, so the `pytest.ini` file looks like this:
```

```

Test discovery is configured to look in *all* `*.py` files for potential
tests, and to treat *only* function names ending in `_check` as tests.
