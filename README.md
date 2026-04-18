# Gleam hooks for pre-commit

[Gleam](https://gleam.run) tools package for [pre-commit](https://pre-commit.com)
and compatible runners like [prek](https://github.com/j178/prek).

These hooks shell out to the `gleam` CLI, so it must already be installed and
on your `PATH` (they use `language: system`).

## Usage

```yaml
-   repo: https://github.com/jtdowney/pre-commit-gleam
    rev: master
    hooks:
    -   id: format
    -   id: check
```

Works the same under `prek`, which reads the standard `.pre-commit-config.yaml`:

```sh
prek install
prek run --all-files
```

## Available hooks

| id             | what it runs           | modifies files | notes                                  |
| -------------- | ---------------------- | -------------- | -------------------------------------- |
| `format`       | `gleam format`         | yes            | Reformats staged `.gleam` files.       |
| `format-check` | `gleam format --check` | no             | Fails if staged files are unformatted. |
| `check`        | `gleam check`          | no             | Type-checks the whole project.         |
| `test`         | `gleam test`           | no             | Runs the project tests.                |

`check` and `test` always run on the whole project and ignore the list of
staged files.

## Passing arguments

```yaml
-   repo: https://github.com/jtdowney/pre-commit-gleam
    rev: master
    hooks:
    -   id: check
        args: ['--target', 'javascript']
```
