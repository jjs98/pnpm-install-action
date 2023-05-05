# pnpm-install-action
Action for Github Workflows that installs pnpm install with a cache

How to use in workflow.yml:

```yaml
name: Build client
on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

defaults:
  run:
    working-directory: src/client

jobs:
  build:
    name: Run pnpm Build
    runs-on: ubuntu-latest
    timeout-minutes: 10
    steps:
      - name: Checkout
        uses: actions/checkout@v3

      - name: Install pnpm
        uses: jjs98/pnpm-install-action@v6
        with:
          directory: src/client

      - name: Build client
        run: pnpm build
```
