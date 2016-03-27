starterkit
===========

This is a meta package intended for new opam switches and for new
OCaml programmers.

# OCaml workflow

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
