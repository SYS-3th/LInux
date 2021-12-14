# nano 명령어

## nano 실행 명령어 예제들

- nano memo.txt___ memo.txt를 편집하기 위해 open한다.
- nano -B memo.txt ___ save 직전에 이전 파일을 ~.filename으로 백업한다.
- nano -m memo.txt ___ cursor 이동을 위해 mouse를 사용한다. (지원시)
- nano +83 memo.txt___ 83 번째 줄부터 편집한다.


## 기본 명령(단축키)들
ctrl+g (F1)___ 도움말 표시
ctrl+x (F2)___ nano 종료 (혹은 현재의 file buffer를 닫음)
ctrl+o (F3)___ 현재 편집 중인 파일 저장
ctrl+j (F4)___ 문단을 justify(행의 끝을 나란히 맞추다)한다. 즉, 한 문단을 한 줄로 붙인다.
ctrl+r (F5) ___ 현재 file에 다른 file의 내용을 추가한다.
ctrl+w (F6)___ text 검색
ctrl+c (F11)___ 현재의 cursor 위치 표시하기
ctrl+t (F12)___ spell check 시작
ctrl+\ ___ search and replace


## 잘라내기/복사/붙여넣기에 관련된 단축키들
- ctrl+k (F9) ___ 현재의 line 혹은 선택된 text 삭제(그리고 저장(copy))
- ctrl+u (F10)___  붙여넣기 (paste)
- ctrl+6  ___ 현재 cursor 위치부터 text 선택 시작. 이후 alt+6로 복사 후 선택 종료. 아니면 다시 ctrl+6를 입력하면 (복사 없이)단순 종료.
- alt+6 ___ 선택 구간 복사. 선택 구간이 없다면 현재 caret 이 있는 한 줄을 복사. 이후 ctrl+u 로 붙여넣기 할 수 있음,



## 화면 이동과 관련된 단축키들 
PageUP 또는 ctrl+y (F7) ___ 이전 화면
PageDown 또는 ctrl+v (F8)___ 다음 화면
alt+( ___ 현재 문단의 시작으로
alt+)___ 현재 문단의 끝으로
alt+= ___ 한 줄 밑으로 스크롤
alt+- ___ 한 줄 위로 스크롤
ctrl+space ___ 한 단어 앞으로
alt+space ___ 한 단어 뒤로 (GUI모드가 아닐 경우)
alt+\___ file의 첫 line으로
alt+/___ file의 마지막 line으로
alt+] ___ 현재 괄호에 match되는 괄호 찾기
ctrl+- ___ 줄 번호와  열을 입력한 후 그곳으로 이동

