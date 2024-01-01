## insert-license-header (-conda) mirror

This pre-commit hook automatically inserts our license header at the beginning of source code files tracked by Git.

Usage: (in `.pre-commit-config.yaml`)

```
repos:
  - repo: https://github.com/Quantco/pre-commit-insert-license
    rev: "1.1.0"
    hooks:
      - id: insert-license
        types: [python]
        args:
          - --dynamic-years
          - --comment-style
          - "#"
```

> :warning: In order for this hook to work properly, ensure that the entire git history is fetched during `pre-commit-checks`.

This hook uses our license header by default.

However, you can overwrite this default header by first creating your own base64 encoded string:
```
$ echo "Copyright (C) 2042, PearCorp, Inc.\nSPDX-License-Identifier: LicenseRef-PearCorp" | base64
Q29weXJpZ2h0IChDKSAyMDQyLCBQZWFyQ29ycCwgSW5jLgpTUERYLUxpY2Vuc2UtSWRlbnRpZmllcjogTGljZW5zZVJlZi1QZWFyQ29ycAo=
```
And then supplying it to the hook:
```
[...]
- id: insert-license
        types: [python]
        args:
          - --license-base64
          - "Q29weXJpZ2h0IChDKSAyMDQyLCBQZWFyQ29ycCwgSW5jLgpTUERYLUxpY2Vuc2UtSWRlbnRpZmllcjogTGljZW5zZVJlZi1QZWFyQ29ycAo="
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

For more configuration options see the conda-packaged tool [insert-license-header](https://github.com/thomasmarwitz/insert-license-header) that exposes the `insert-license-header` executable, the original repository [Lucas-C/pre-commit-hooks](https://github.com/Lucas-C/pre-commit-hooks) and [Pre-Commit](https://pre-commit.com/).
