# git
명령어
+ git init
    + git 하위 디렉토리 생성(폴더를 만든 후, 그 안에서 
    명령 실행=>새로운 git 저장소 생성)
+ git clone 

    + 사용자명@호스트:/원격/저장소/경로
    + 원격 서버 저장소 복제
    ```
     git clone [url]
    ```
    url에는 클론해올 저장소의 주소를 지정해줍니다.
+ git add
    + `git add`명령어는 다음 변경(commit)을 기록할 때까지 변경분을 모아놓기 위해서 사용합니다. 
+ git status
    + `git add`명령어를 사용할 때, 항상 함께 사용되는 명령어입니다.
    `git status`는 작업 디렉토리의 상태를 확인하기 위해서 사용합니다.
+ git commit
    + 사용법
        + git commit -m "메시지"
    + `git commit`을 사용할 때는 커밋 메시지를 함께 작성해야한다.
        + 좋은 커밋 메시지 작성법
            1. 커밋 유형 지정
            ```
                1. FEAT : 새로운 기능의 추가
                2. FLX: 버그 수정
                3. DOCS: 문서수정
                4. STYLE: 스타일 관련 기능
                5. REFACTOR: 코드 리펙토링
                6. TEST: 테스트 코드
                7. CHORE : 빌드 없무 수정, 패키지 매니저 수정
            ```
            2. 제목 행을 50자로 제한
                + 강제로 제한하는 것은 아니고 읽기 쉽고 간결하게 표현하기 위한 규칙이다
            3. 제목 행의 첫 글자는 대문자로 시작
                + docs file ❌
                + Docs file ⭕
            4. 제목 행 끝에 마침표는 넣지 않는다
                + Open the door. ❌
                + Open the door  ⭕
            5. 제목은 설명하듯이 명령문을 작성
                + 네 방을 치우다(Clean your room)
                + 책을 본다(Read a book)
+ git status
    + 현자 파일의 상태를 확인
    + `git add`와 `git commit`등의 명령을 실행 결과를 확인하는 것 뿐이다.
+ git branch
    + `branch`란 여러 개발자들이 동시의 다양한 작업을 할 수 있게 만들어 주는 기능을 말한다.
    + 각자의 작업 영역에서 소스코드 변경이 가능하다
    + 작업한 내용을 다시 새로운 하나의 브랜치로 모을 수 있습니다.
+ git push origin main
    + 변경사항을 서버에 업로드