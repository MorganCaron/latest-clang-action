# Latest Clang for Github Actions
GitHub action to provide a precompiled version of LLVM Clang for continuous integration without having to recompile at each run.

![Github Stars](https://img.shields.io/github/stars/MorganCaron/clang-precompiled-action?style=for-the-badge)
![Github Forks](https://img.shields.io/github/forks/MorganCaron/clang-precompiled-action?style=for-the-badge)
[![Discord](https://img.shields.io/discord/268838260153909249?label=Chat&logo=Discord&style=for-the-badge)](https://discord.gg/mxZvun4)
[![License](https://img.shields.io/github/license/MorganCaron/clang-precompiled-action?style=for-the-badge)](https://github.com/MorganCaron/CppUtils/blob/master/LICENSE)

### Project Health
![Build](https://img.shields.io/github/actions/workflow/status/MorganCaron/clang-precompiled-action/main.yml?style=for-the-badge&logo=linux&logoColor=white&label=Build)

### Usage

```yml
name: "Build with latest Clang"

on: [ push, pull_request ]

jobs:
  build:
    name: "Latest Clang"
    steps:
    - uses: actions/checkout@v4
    - uses: MorganCaron/latest-clang-action@master

    - name: Compile
      run: |
        clang++ -o test test.cpp

    - name: Run
      env:
        LD_LIBRARY_PATH: ${{ github.workspace }}/llvm/lib/x86_64-unknown-linux-gnu
      run: |
        ./test
```

Or with [XMake](https://xmake.io/):
```yml
name: "Build with latest Clang"

on: [ push, pull_request ]

jobs:
  build:
    name: "XMake + Latest Clang"
    steps:
    - uses: actions/checkout@v4
    - uses: MorganCaron/latest-clang-action@master
    - uses: xmake-io/github-action-setup-xmake@v1

    - name: Compile
      run: |
        xmake f --toolchain=llvm --sdk=llvm/
        xmake build -vD

    - name: Run
      env:
        LD_LIBRARY_PATH: ${{ github.workspace }}/llvm/lib/x86_64-unknown-linux-gnu
      run: |
        xmake run
```
