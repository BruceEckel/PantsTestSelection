python_sources(
    name="lib",
)

python_tests(
    name="testing",  # Try using a different name
    description='''
    `*.py` tells Pants to examine all files when looking for tests.
    When looking inside all files for tests, you must explicitly
    call out files to ignore---even standard files like __init__.py.
    ''',
    sources=["*.py", "!__init__.py", "!not_test.py", "!test_not.py"],
)
