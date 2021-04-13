# gha

[![CI](https://github.com/vglen/gha/actions/workflows/ci.yaml/badge.svg)](https://github.com/vglen/gha/actions/workflows/ci.yaml)

```yml
      - name: Checkout GitHub actions repo
        uses: actions/checkout@v2
        with:
          repository: vglen/gha
          path: .github/actions
          ref: main
```