# Nengo에 기여하기

\[컨트리뷰터를 위한 안내서\]\(\)를 먼저 읽어주세. 아래의 설명은 `nengo` 프로젝트에 적용됩니다.

### 개발자용 설치

만약 nengo의 일부를 변경하고싶다면, 개발자용 설치와 의존성 설치를 해야합니다.

```text
git clone https://github.com/nengo/nengo.git
cd nengo
pip install -e '.[all]' --user
pre-commit install
```

만약 가상 환경이라면 `--user` 플래그를 생략할 수 있습니다.

### 단위 테스트를 실행하는 방법

nengo에는 [pytest](https://docs.pytest.org/en/latest/)로 실행되는 대규모 테스트 스위트가 포함되어 있습니다. 테스트 실행은 다음과 같습니다.

```text
pytest --pyargs nengo
```

### 개별 테스트 실행

해당 파일에서 `pytest`를 호출하여 특정 테스트 파일의 테스트를 실행할수 있습니다. 예를 들어,

```text
pytest nengo/tests/test_node.py
```

는 `test_node.py` 의 모든 테스트를 실행합니다. 

개별 테스트는 `-k EXPRESSION` 인수를 사용합니다. 주어진 부분 문자열 표현과 일치하는 테스트만 실행합니다. 예를들어,

```text
pytest nengo/tests/test_node.py -k test_circular
```

는 `test_node.py` 파일에서 `test_circular` 테스트를 실행합니다.

### 테스트 결과 표시

많은 nengo 테스트는 쉬운 디버깅을 위해 테스트 결과를 표시하는 기능을 내장하고 있습니다. 이 기능을 활성화하려면, `--plots`를 `pytest`에 전달하세요. 예를들어 다음과 같습니다.

```text
pytest --plots --pyargs nengo
```

어느 `pytest`디렉토리에서 실행하더라도, nengo.simulator.plots에 표시되며, 다음과같이 디렉토리를 설정할수도 있습니다.

```text
pytest --plots=path/to/plots --pyargs nengo
```

### 도움말 및 기타 옵션

`pytest` 사용법 및 Nengo특정 옵션에 대한 정보는 다음과 같이 찾을수 있습니다.

```text
pytest --pyargs nengo --help
```

### 테스트 작성하기

자체 테스트를 작성할 때, 기존 테스트와 잘 통합하기 위해 커스텀 nengo \[fixtures\]와 \[markers\]를 사용하세요. 예를들어 다음과같이 기존 테스트를 살펴보거나 의논하세요.

```text
pytest --pyargs nengo --fixtures
```

```text
pytest --pyargs nengo --markers
```

### 문서 빌드 방법

이 문서는 \[developer installation\]에 속해 있는 Sphinx로 작성되었습니다.

그러나 문서에 포함된 Jupyter노트북을 빌드하기위한 추가 요구사항인 [Pandoc](https://pandoc.org/)이 있습니다. 패키지 관리자\(예: Homebrew, `apt`\)를 사용하는 경우 패키지 관리자를 통해 [Pandoc](https://pandoc.org/)을 설치할수 있으며, 그렇지 않으면 [이 페이](https://pandoc.org/installing.html) 의 설명을 참조하세요.

모든 요구사항을 설치한 후, 문서를 빌드하기 위해 `nengo`의 루트 디렉토리에서 다음 명령어를 실행하세요. 모든 예제가 문서 빌드 과정의 일부로 실행되기 때문에 이 작업은 몇분정도 걸립니다.

```text
sphinx-build -vW docs docs/_build
```

환경에 따라 예제 빌드에 사용되는 Jupyter 커널을 설정해야 할 수도 있습니다. 커널을 설정하려면 다음 명령을 사용하세요.

```text
sphinx-build -vW docs docs/_build -D nbsphinx_kernel_name=<kernelname>
```

### 도움 구하기

nengo 개발에 대한 질문이 있거나 nengo와 `git`이 제시하는 학습곡선을 어떻게 잘 오를수 있는지 궁금하다면, [Nengo 포럼](https://forum.nengo.ai)으로 오세요. 최선을 다해 도와드리겠습니다!

