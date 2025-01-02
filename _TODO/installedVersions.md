# Installed Versions

Write up how to get the installed versions of modules/libraries for languages that have that concept.

```text
Python 3.10.16 (main, Dec  5 2024, 00:14:55) [GCC 10.2.1 20210110] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import pyspark
>>> pyspark.__version__
'3.3.2'
```

In some cases `__version__` is not an option. Try

```bash
pip show mysql-connector-python
```
