# Development Operations for a Machine Learning Project

This readme will serve as a progress report for all tasks. Original readme can be found [here](OVERVIEW.md).

## Task 0

The first things done with this repo are some initial steps that include:
- Setting up the repo according to instructions provided [here](OVERVIEW.md#2-working-with-the-git-repository)
- Setting up a Dockerfile to containerize the project
- Copying project files from previous laboratories
- Creating this readme

All these steps were done on `feature/task_0` branch.

## Task 1

Installed `black` with Jupyter Notebook support by adding `pip install "black[jupyter]"` to the `Dockerfile`. The tool was run inside the container using the following command:
```bash
black --line-length 120 $PWD
```
The code was successfully reformatted.

## Task 2

Installed `pre-commit` with Jupyter Notebook support by adding `pip install pre-commit` to the `Dockerfile`. Installed and tested with:

```bash
# Register the hook
pre-commit install
# Run the pre-commit on all files
pre-commit run --all-files
```

Recommended lines were added to `.pre-commit-config.yaml` with one additional hook:

```yaml
  # Black formatter
  - repo: https://github.com/psf/black
    rev: 24.4.0
    hooks:
      - id: black
        args: ["--line-length=120"]

  # Black formatter for Jupyter Notebooks
  - repo: https://github.com/nbQA-dev/nbQA
    rev: 1.1.1
    hooks:
      - id: nbqa-black
        name: nbqa-black
        description: "Run 'black' on a Jupyter Notebook"
        entry: nbqa black
        language: python
        require_serial: true
        types: [jupyter]
        additional_dependencies: [black]
        args: ["--line-length=120"]

  # Codespell - Fix common misspellings in text files.
  - repo: https://github.com/codespell-project/codespell
    rev: v2.2.6
    hooks:
      - id: codespell
        args: ["--skip=*.ipynb"]

  # Pyupgrade - automatically upgrade syntax for newer versions of the language.
  - repo: https://github.com/asottile/pyupgrade
    rev: v3.15.2
    hooks:
      - id: pyupgrade
        args: [--py310-plus]

```

`codespell` will ignore `.ipynb` files, because otherwise it produces weird errors that prevent user from committing changes. `--write-changes` flag appeared to do nothing so it was removed.

## Task 3

TODO

## Task 4

TODO

## Task 5

TODO

## Task 6

TODO
