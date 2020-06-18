# 컨트리뷰터를 위한 안내서

모든 종류의 기여를 환영합니다! 아래의 목록은 완전한 것이 아닙니다.

* **만들기** : Nengo를 사용하여 모델을 만들고 커뮤니티와 공유하세요.
* **버그 보고** : Nengo가 충돌하거나 예상치 못한 일을 한다면 알려주세요.
* **개발** : Nengo 프로젝트에 일부 코드를 추가하거나 수정하세요.
* **문서** : 문서를 추가하거나 명확하게하여 Nengo 사용 방법을 다른 사람들에게 가르쳐주세요.

### 창작물 공유

Nengo 창작물을 커뮤니티와 공유하는 방법에는 여러 가지가 있습니다. 가장 빠른 방법은 포럼에 글을 올리는 것입니다.

1. \[the examples category of the forum\]으로 이동하세요.
2. 아직 계정이 없으면 페이지 오른쪽 상단에있는 "Sign Up" 버튼을 클릭하세요.
3. 오른쪽 상단에있는 "New Topic" 버튼을 클릭하세요.
4. 팝업 편집기로 게시물을 작성하고, \[Markdown\]\([https://commonmark.org/help/](https://commonmark.org/help/)\)으로 게시물 형식을 지정하세요. - 코드 블록을보다 쉽게 ​​읽을 수 있도록 형식을 지정합니다.

창작물이 포럼 게시물에 비해 너무 큰 경우 \[예제 저장소\]에서 풀 리퀘스트 하는 것을 고려하세요.

### 버그 보고 및 기능 제안

Nengo 프로젝트에서 버그를 발견하거나 특정 기능이 필요하다고 생각되면 프로젝트의 Github 저장소에 이슈를 제출하세요.

1. 프로젝트의 Github 페이지 \(예 : \[nengo/nengo-gui\]\([https://github.com/nengo/nengo-gui](https://github.com/nengo/nengo-gui)\) \)로 이동하세요.
2. 페이지 상단의 "이슈" 탭을 클릭하세요.
3. 페이지 오른쪽 상단에있는 녹색의 "새 이슈"버튼을 클릭하세요.

이슈를 제출할 때, 특히 버그를 보고할 때 최대한 자세하게 설명하세요. 버그를 해결하기 위해 가장 먼저해야 할 일은 로컬에서 버그를 재현하는 것입니다. 버그를 재현하기 위해 가장 짧은 스크립트 또는 일련의 단계를 찾아보세요.

### 풀 리퀘스트

창작물을 공유하거나 Nengo 프로젝트를 개발하거나 문서를 추가 할 때 \[풀 리퀘스트\]\([https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests)\)로 기여를 관리 합니다 .

1. 기여할 \[저장소를 포크\]하고 로컬에서 복제 하세요.
2. 저장소를 변경하기 전에 변경을위한 새 브런치를 생성하세요. `master` 브런치에서 코드를 편집해서는 안됩니다! 브런치를 생성하려면 다음 명령을 사용하세요.

   ```text
   git checkout -b <branch name>
   ```

   브런치에 의미있는 이름을 부여하세요. `patch` 또는 `fix128` 같은 이름은 나중에 기억하기 어렵습니다.

3. 저장소를 변경하세. 변경 사항이 크면 변경 사항을 별도의 의미있는 커밋으로 나누세요.

   ```text
   git add <files>
   git commit
   ```



   커밋 메시지 형식을 포함하여 스타일 가이드를 따르세요.

4. 변경이 끝나면 Github에 푸시하세요.

   그리고 Nengo 프로젝트의 저장소에 \[풀 리퀘스트\] 하세요.

   ```text
   git push origin <branch name>
   ```

5. 풀 리퀘스트는 최소한 한 번의 검토를 받습니다. 검토는 여러 번 반복 될 수있는 절차입니다. 리뷰에 응답 할때는 \[행동 강령\]을 따르세요.

