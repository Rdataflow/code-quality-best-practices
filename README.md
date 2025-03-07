# code-quality-best-practices
best practice guidelines on how to achieve high code quality (WIP)

## CI tests
Introduce CI tests for
- unit tests
- end-to-end tests

## Monitor code quality
There are plenty tools to monitor and rate code quality, i.e.
- https://sonarcloud.io

## Scripting
Python, Bash and whichever tool is used, in basic scripting the following concepts matter

### Concepts

#### callable scripts
* anyone may call and execute my script directly (i.e. using `./myscript.py`)
* [ ] add the appropriate [shebang](https://en.wikipedia.org/wiki/Shebang_(Unix)) on line 1 of your script
  ```python
  #!/usr/bin/env python
  ```
* [ ] make script executable
  ```bash
  chmod +x ./myscript.py
  ```

#### dynamic paths
* anyone may call your script from any directory
* [ ] use dynamic path detection to infer location of your data within this folder or subfolders
  ```python
  BASEDIR = os.path.dirname(__file__)
  DATAFILE = os.path.join(BASEDIR, "data.csv")
  CONFIGFILE = os.path.join(BASEDIR, "config.json")
  ```

#### exceptions and return state
* any caller (i.e. a CI test) may check the return state
* [ ] ensure any invalid case is caught and the appropriate exception is raised
  ```python
  valid = some_validation_function(...)
  assert valid
  ```
