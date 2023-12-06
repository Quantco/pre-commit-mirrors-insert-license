insert-license-header (-conda) mirror


Usage: (in `.pre-commit-config.yaml`)

```
- repo: https://github.com/Quantco/pre-commit-insert-qc-license
    rev: 1.0.0
    hooks:
      - id: insert-license
        files: \.py$
        args:
          - --dynamic-years
          - --comment-style
          - "#"
```

Other comment styles:
For Java / Javascript / CSS/ C / C++ (multi-line comments) set: `/*| *| */`
For Java / Javascript / C / C++ (single line comments) set `//`
For HTML files: `<!--|  ~|  -->`

To remove all license headers, temporarily add the `--remove-header` arg in
your `.pre-commit-config.yaml`. Run the hook on all files: `pre-commit run insert-license -a`.

For more configuration options see [Lucas-C/pre-commit-hooks](https://github.com/Lucas-C/pre-commit-hooks) and [Pre-Commit](https://pre-commit.com/)
