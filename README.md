## insert-license-header (-conda) mirror

This pre-commit hook automatically inserts our license header at the beginning of source code files tracked by Git.

Usage: (in `.pre-commit-config.yaml`)

```
repos:
  - repo: https://github.com/Quantco/pre-commit-insert-license
    rev: "1.0.1"
    hooks:
      - id: insert-license
        types: [python]
        args:
          - --license-base64
          - "Q29weXJpZ2h0IChjKSBRdWFudENvIHt5ZWFyX3N0YXJ0fS17eWVhcl9lbmR9ClNQRFgtTGljZW5zZS1JZGVudGlmaWVyOiBMaWNlbnNlUmVmLVF1YW50Q28K"
          - --dynamic-years
          - --comment-style
          - "#"
```


The string contained in the example is a base64 encoded string of the license header we want to use:
```
$ echo "Copyright (c) QuantCo {year_start}-{year_end}\nSPDX-License-Identifier: LicenseRef-QuantCo" | base64
Q29weXJpZ2h0IChjKSBRdWFudENvIHt5ZWFyX3N0YXJ0fS17eWVhcl9lbmR9ClNQRFgtTGljZW5zZS1JZGVudGlmaWVyOiBMaWNlbnNlUmVmLVF1YW50Q28K
```

Other comment styles:
For Java / Javascript / CSS/ C / C++ (multi-line comments) set: `/*| *| */`
For Java / Javascript / C / C++ (single line comments) set `//`
For HTML files: `<!--|  ~|  -->`

To remove all license headers, temporarily add the `--remove-header` arg in
your `.pre-commit-config.yaml`. Run the hook on all files: `pre-commit run insert-license -a`.

For more configuration options see the conda-packaged tool [insert-license-header](https://github.com/thomasmarwitz/insert-license-header) that exposes the `insert-license-header` executable, the original repository [Lucas-C/pre-commit-hooks](https://github.com/Lucas-C/pre-commit-hooks) and [Pre-Commit](https://pre-commit.com/).
