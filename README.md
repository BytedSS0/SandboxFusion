# Code Sandbox

A secure sandbox for running and judging code generated by LLMs.

Please view the complete documentation at https://bytedance.github.io/SandboxFusion/ .

## Table of Contents

- [Features](#features)
- [Contributing](#contributing)
- [License](#license)

## Features

**Code Runner**: Run and return the result of a code snippet

Supported languages:

- Python (python, pytest)
- C++
- C#
- Go (go, go test)
- Java (javac, junit)
- NodeJS
- Typescript (tsx, jest)
- Scala
- Kotlin
- PHP
- Rust
- Bash
- Lua
- R
- Perl
- D
- Ruby
- Julia
- Verilog
- CUDA (GPU)
- Python (GPU)

Jupyter mode kernels:

- python3

**Online Judge**: Implementation of Evaluation & RL datasets that requires code running

- [HumanEval](https://github.com/openai/human-eval)
- [MultiPL-E HumanEval](https://github.com/nuprl/MultiPL-E)
- [Shadow Humaneval](https://huggingface.co/datasets/Miaosen/openai-humaneval-sky-shadow)
- [CodeContests](https://github.com/google-deepmind/code_contests)
- [MBPP](https://github.com/google-research/google-research/tree/master/mbpp)
- [MBXP](https://github.com/amazon-science/mxeval)
- [MHPP](https://github.com/SparksofAGI/MHPP)
- [CRUXEval](https://github.com/facebookresearch/cruxeval)
- [NaturalCodeBench](https://github.com/THUDM/NaturalCodeBench)
- [PAL-Math](https://github.com/deepseek-ai/DeepSeek-Coder/tree/main/Evaluation/PAL-Math)
- [verilog-eval](https://github.com/NVlabs/verilog-eval)

## Contributing

### Installation

**Docker**

Build the image locally:

```bash
docker build -f ./scripts/Dockerfile.base -t code_sandbox:base
# change the base image in Dockerfile.server
sed -i '1s/.*/FROM code_sandbox:base/' ./scripts/Dockerfile.server
docker build -f ./scripts/Dockerfile.server -t code_sandbox:server
docker run -d --rm --privileged -p 8080:8080 code_sandbox:server make run-online
```

**Manual**

Prerequisites: [conda](https://conda.io/projects/conda/en/latest/user-guide/install/index.html), [poetry](https://python-poetry.org/docs/#installation)

To install the sandbox service:

```bash
conda create -n sandbox -y python=3.12
conda activate sandbox
poetry install
make run-online
```

Please refer to `scripts/Dockerfile.base` for the runtime of each supported language, and `scripts/Dockerfile.server` for the installation of extra packages for python and nodejs.

### Dev & Test

Refer to installation section for the setup of development environment.

Run all unit tests:

```bash
make test
```

Run a specific unit test (allows you to see stdout):

```bash
make test-case CASE=test_java_assert
```

Format the code:

```bash
make format
```

## License

```
Copyright 2024 Bytedance Ltd. and/or its affiliates

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
