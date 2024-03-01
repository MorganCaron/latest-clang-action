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
    name: "Clang"
    steps:
    - uses: actions/checkout@v4
    - uses: MorganCaron/latest-clang-action@master
    - name: Compile
      env:
        CC: "clang"
        CXX: "clang++"
      run: |
        clang++ -o test test.cpp
        ./test
    - name: Run
      run: |
        ./test
```
