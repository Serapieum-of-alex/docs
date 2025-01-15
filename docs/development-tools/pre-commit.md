```yaml
fail_fast: true
repos:
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v5.0.0
    hooks:
      - id: check-toml
        name: "[py -  check] check toml"
      - id: end-of-file-fixer
        name: "[py -  check] validate yaml"
      - id: no-commit-to-branch
        name: "[git -  check] no commit to branch"
        args: [ --branch=main ]
      - id: trailing-whitespace
        name: "[file - format] trim trailing whitespace"
        args: [ --markdown-linebreak-ext=md ]
      - id: check-added-large-files
        name: "[file -  check] large file"
        args: [ --maxkb=2000 ]
      - id: check-docstring-first
        name: "[py   -  check] docstring first"
        files: /examples
        types : [file, python ]
      - id: check-json
        name: "[json -  check] validate json"
      - id: check-merge-conflict
        name: "[git  -  check] merge conflict"
      - id: debug-statements
        name: "[py   -  check] debug statements"
      - id: detect-private-key
        name: "[cred -  check] private keys"
      - id: fix-encoding-pragma
        name: "[file - format] coding pragma"
        args: [ --remove ]
      - id: mixed-line-ending
        name: "[file - format] mixed line ending"
        args: [ --fix=auto ]
      - id: pretty-format-json
        name: "[json - format] pretty json"
        args: [ --autofix,
                --indent=4,
                --no-sort-keys ]
      - id: requirements-txt-fixer
        name: "[reqs - format] fix requirements.txt"
      - id: check-yaml
        name: "[yaml -  check] validate yaml"
  - repo: https://github.com/pycqa/flake8
    rev: 7.1.1
    hooks:
      - id: flake8
        additional_dependencies: [Flake8-pyproject]
        name: "[py   - check] flake8"
        exclude: ^(examples/|tests/)
#   - repo: https://github.com/pycqa/docformatter
#     rev: v1.4
#     hooks:
#      - id: docformatter
#        name: "[py   - format] docformatter"
#        description: 'Formats docstrings to follow PEP 257.'
#        entry: docformatter
#        args: [-i]
#        language: python
#        types: [python]
#   - repo: https://github.com/pycqa/pydocstyle
#     rev: 6.3.0
#     hooks:
#       - id: pydocstyle
#         name: "[py   - check] pydocstyle"
#         files: ^hydrolib/.*\.py$
  - repo: https://github.com/pycqa/isort
    rev: 5.13.2
    hooks:
      - id: isort
        name: "[py   - format] isort"
  - repo: https://github.com/psf/black
    rev: 24.10.0
    hooks:
      - id: black
  - repo: https://github.com/lovesegfault/beautysh
    rev: v6.2.1
    hooks:
      - id: beautysh
        name: "[bash - format] beautysh"

  - repo: https://github.com/detailyang/pre-commit-shell
    rev: 1.0.5
    hooks:
      - id: shell-lint
        name: "[bash -   lint] shell-lint"

  - repo: https://github.com/rlindsgaard/pre-commit-commit-msg-hooks
    rev: 0.1.0
    hooks:
      - id: check-description-max-length
        name: "[bash -   format] check-description-max-length"
      - id: check-second-line-empty
        name: "[bash -   format] check-second-line-empty"
      - id: check-summary-capitalized
        name: "[bash -   format] check-summary-capitalized"
      - id: check-summary-imperative
        name: "[bash -   format] check-summary-imperative"
      - id: check-summary-max-length
        name: "[bash -   format] check-summary-max-length"
      - id: check-summary-punctuation
        name: "[bash -   format] check-summary-punctuation"

  - repo: https://github.com/PyCQA/bandit
    rev: 1.7.5
    hooks:
      - id: bandit
        args: ["--skip=B101"]

  - repo: https://github.com/gitleaks/gitleaks
    rev: v8.17.0
    hooks:
      - id: gitleaks

  - repo: https://github.com/Yelp/detect-secrets
    rev: v1.4.0
    hooks:
      - id: detect-secrets
  - repo: https://github.com/bridgecrewio/checkov
    rev: 2.1.63
    hooks:
      - id: checkov

  - repo: https://github.com/trufflesecurity/truffleHog
    rev: v3.88.2
    hooks:
      - id: trufflehog

  - repo: local
    hooks:
      - id: safety
        name: Safety Check
        entry: safety check --full-report
        language: system
        types: [python]
        pass_filenames: false

  - repo: local
    hooks:
      - id: pytest-check
        name: pytest-check
        entry: pytest -vvv --cov=hydrolib --cov-report term-missing
        language: system
        pass_filenames: false
        always_run: true

  - repo: local
    hooks:
      - id: examples-notebook-check
        name: nbval
        entry: pytest --nbval
        language: system
        files: \.ipynb$

  - repo: local
    hooks:
      - id: doctest
        name: doctest
        entry: pytest --doctest-modules
        language: system
        files: ^hydrolib/.*\.py$

```