[![test](https://github.com/giampaolo/SublimeLinter-makefile/actions/workflows/tests.yml/badge.svg)](https://github.com/giampaolo/SublimeLinter-makefile/actions/workflows/tests.yml)

About
=====

A plugin for [SublimeLinter](https://github.com/SublimeLinter/SublimeLinter),
for linting **Makefiles**. What it checks:

Checkers
========

This plugin is able to detect the following error conditions:

#### Undefined global variable names

Correct:

```makefile
FOO = 1
test:
    echo $(FOO)

```

Incorrect (prints `undefined name "FOO"`):

```makefile
test:
    echo $(FOO)
```

#### Undefined target names

Correct:

```makefile
clean:
    rm -rf build/*

test:
    ${MAKE} clean
    pytest .

```

Incorrect (prints `undefined target "clean"`):

```makefile
test:
    ${MAKE} clean
    pytest .
```

#### Missing `.PHONY` directive

This will print `missing .PHONY declaration` if there's a file or directory
named "test" in the same directory as the Makefile:

```makefile
test:
    pytest .
```

#### Use of spaces instead of tabs

Any line starting with a space instead of tab will produce a warning.
