# PyBase - DB Manager
![Issues](https://img.shields.io/github/issues/NTBBloodbath/PyBase)
![Forks](https://img.shields.io/github/forks/NTBBloodbath/PyBase)

![Python Versions](https://img.shields.io/pypi/pyversions/pybase-db)
![Version](https://img.shields.io/pypi/v/pybase-db?color=green&label=version)
[![Downloads](https://pepy.tech/badge/pybase-db)](https://pepy.tech/project/pybase-db)

![License](https://img.shields.io/pypi/l/pybase-db)

![PyBase](https://socialify.git.ci/NTBBloodbath/PyBase/image?description=1&descriptionEditable=Python%20DataBase%20Manager%20for%20multiple%20filetypes%20including%20SQLite3.&font=Inter&forks=1&issues=1&logo=https%3A%2F%2Fiili.io%2FFEHkLg.png&owner=1&pattern=Circuit%20Board&stargazers=1&theme=Light)

PyBase is a DataBase Manager for multiple filetypes including SQLite3.

It's focused on the ease and effectiveness for the administration of databases.

------

## Why PyBase?
**If you want to store** static **data** (JSON, YAML, TOML, Bytes) **or store a database in SQLite3**,
**the best thing would be to use an administrator that simplifies your tasks and
helps you with a good organization and efficiently.**

**PyBase does exactly that, allows you to create such databases with
just one method, and simplifies the task of manipulating their data!**

------

## Contribuitors
- [Danny2105](https://github.com/Danny2105)

------

# Quick start
## Installation
PyBase requires Python 3.x and can be installed through `pip` with the following command.
```sh
# Stable version
python3 -m pip install -U pybase_db

# Pre-release (Development) version
python3 -m pip install -U --pre pybase_db

# From github's latest commit
# Available branches:
#   • master (recommended)
#   • development (unstable releases)
# NOTE: this installation mode will not install PyBase dependencies!
python3 -m pip install -U git+https://github.com/NTBBloodbath/PyBase@branch
```

### Building
The development branch changes aren't compiled and uploaded to Pypi every time,
so you must compile a wheel yourself to test the experimental stuff if the newest
changes aren't uploaded to Pypi.
```sh
python3 setup.py bdist_wheel

python3 -m pip install -U dist/pybase_db-version-py3-none-any.whl
```

## Usage example
This is a brief example of the methods that PyBase currently has.
```py
# Lets import PyBase Class from PyBase Package
from pybase_db import PyBase

# Lets define our database name and format (with default db_path).
# db_type isn't case sensitive. You can use JSON and json and it'll be valid.
db = PyBase(database="example", db_type="JSON")  # => ./example.json

# Lets define and add some content to our database.
pybase_info = {"pybase": "awesomeness", "version": "1.0.0"}

# Lets insert the defined dict inside our database.
db.insert(pybase_info,
          mode="w")  # => {'pybase': 'awesomeness', 'version': '1.0.0'}

# Lets delete an object inside our database cuz it's useless.
db.delete('pybase')  # => {'version': '1.0.0'}

# Lets insert more data cuz that's funny!
db.insert(content={"guilds": {}, "ownerID": 1234567890}, mode="w")

# Lets insert some data inside the guilds key
db.insert(content={
    "guilds": {
        "12345": {
            "name": "First guild"
        },
        "67890": {
            "name": "Second guild"
        }
    }
},
          mode="a")

# Lets fetch an object inside our database and display its type.
# It's useful to debug and manipulate the data dynamically.
db.fetch('version')  # => <class 'str'>

# Gets the corresponding value according to the specified key
db.get("version")  # => '1.0.0'

# New data of the new update
pybase_update = {"pybase": {"newVersion": {"version": "1.0.0"}}}
db.insert(pybase_update)

# Get all data from db
db.get()  # => {'pybase': {'newVersion': {'version': '1.0.0'}}, 'version': '1.0.0'}

# Get the values using its key
db.get("pybase")  # => {'newVersion': {'version': '1.0.0'}}

# Get a value of a key separated by a period (.)
db.get("pybase.newVersion")  # => {'version': '1.0.0'}

# Several
db.get("pybase.newVersion.version")  # => 1.0.0
```

> **To see SQLite3 usage example, click [here](./examples/pysql_usage.py)**

## Benchmark
PyBase is made to be fast, and what better proof than a benchmarking test?
> Note: you can see the code used for the test in [tests](./tests/benchmark.py)

```
creating        took 0.002 seconds to complete its execution.

insert_1        took 0.004 seconds to complete its execution.

insert_2        took 0.004 seconds to complete its execution.

deleting        took 0.008 seconds to complete its execution.

fetching        took 0.003 seconds to complete its execution.

getting_one     took 0.003 seconds to complete its execution.

getting_all     took 0.003 seconds to complete its execution.

pushing_1       took 0.005 seconds to complete its execution.

updating        took 0.004 seconds to complete its execution.
```

## Documentation
You can see the PyBase documentation through the `help()` function of the REPL
and through the [official documentation site](https://pybase.github.io/docs/).

## Changelog
You can see the PyBase changelog [here](./CHANGELOG.md)

------

# License
**PyBase is distributed under MIT License.**

# Contributing
You can see how to contribute [here](./CONTRIBUTING.md)

# Code of Conduct
You can see the code of conduct [here](./CODE_OF_CONDUCT.md)
