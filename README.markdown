starterkit
===========

This is a meta package intended for new opam switches and for new
OCaml programmers.

Get a switch ready with:

```shell
$ opam install starterkit
```

It installs `lambda-term`, `ocp-indent`, `stringext`, `utop`,
`ocp-index`, `merlin`, `ocamlfind`, `oasis`, `ocamlbuild`.

# OCaml workflow

Use `oasis` to get a project up and running quickly, example `_oasis`
file:

```text
OASISFormat:  0.4
OCamlVersion: >= 4.02.0
Name:         opam_package_name
Version:      0.1.0
Maintainers:  New OCaml programmer
Homepage:     http://my_coolsite.com
Synopsis:     Some short description
Authors:      Cool@me.com
License:      BSD-3-clause
Plugins:      META (0.4), DevFiles (0.4)
AlphaFeatures: ocamlbuild_more_args

Description:
Some cool description

# This is a comment and this below creates an binary program
Executable <some_program_name>
  Path: src
  BuildTools:ocamlbuild
  install: true
  MainIs: main.ml
  CompiledObject: native
  BuildDepends: package_one, package_two

# Another comment, this builds a library called pg
Library pg
  Path:         src
  # oasis will figure out the dependencies,
  # Just list the modules you want public,
  # Note that there's no .ml, just give the name
  Modules:      Pg
  CompiledObject: best
  BuildDepends: some_package, another_package

# Here's one that uses C/C++ code, adapt as needed
Library lib_with_c
  Path: src
  BuildTools:ocamlbuild
  install: true
  CClib: -L/usr/local/lib -lfoo -lbar -lstdc++
  CCOpt: -g -Wall -std=c++11 -x c++ -I/usr/local/include
  NativeOpt: -cc g++
  ByteOpt: -cc g++
  Modules: Some_lib
  CompiledObject: best
  CSources: some_lib_stubs.c
  BuildDepends: opam_lib1, opam_lib2
```

Auto generate everything with:

`oasis setup -setup-update dynamic`

then a simple

`make` builds your project.

Use `ocp-browser` to show you type signatures/documentation of
installed OCaml code:

```shell
$ ocp-browser
```

![](./images/ocp-browser.png)

Use `ocp-indent` to align your code, `vim/emacs` need to add code to
their startup code.

An example `~/.ocp-indent` file:

```text
base = 2
type = 2
in = 0
with = 0
match_clause = 2
max_indent = 4
strict_with = never
strict_else = always
strict_comments = false
align_ops = true
align_params = auto
syntax = lwt
```

Use `utop` for a great repl experience:

```shell
$ utop
```

![](./images/utop.png)

Use `merlin` for code completion in your projects, just have a
`.merlin` file in your project root and editor support from
`vim/emacs`. 

![](./images/merlin.png)

Example `.merlin` file (`B` is for compiled built code path, `S` is
for source)

```text
B some_path1
S some_path2
PKG opam_pkg1 opam_pkg2
FLG -w +a-4-40..42-44-45-48
```
