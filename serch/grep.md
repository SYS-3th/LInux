# grep명령어

- grep "STR" [FILE] ___ 대상 파일에서 문자열 검색
- grep "STR" *___ 현재 디렉토리 모든 파일에서 문자열 검색	
- grep "STR" *.ext___ 특정 확장자를 가진 모든 파일에서 문자열 검색	
- grep -i "STR" [FILE] ___ 대소문자 구분하지 않고 문자열 검색	
- grep -v "STR" [FILE] ___ 매칭되는 PATTERN이 존재하지 않는 라인 선택
-	grep -w "STR" [FILE] ___ 단어(Word) 단위로 문자열 검색
- grep -n "STR" [FILE] ___ 검색된 문자열이 포함된 라인 번호 출력
- grep -r "STR" *___ 하위 디렉토리를 포함한 모든 파일에서 문자열 검색	
- grep -m 100 "STR" FILE ___ 최대 검색 결과 갯수 제한	
- grep -H "STR" * ___ 검색 결과 앞에 파일 이름 표시	
- grep "A.*B" * ___ 문자열 A로 시작하여 문자열 B로 끝나는 패턴 찾기	
- grep "STR[0-9]" * ___ 0-9 사이 숫자만 변경되는 패턴 찾기
- grep -F "*[]?..." [FILE] ___ 문자열 패턴 전체를 정규 표현식 메타 문자가 아닌 일반 문자로 검색하기
- grep "\*" [FILE] ___ 정규 표현식 메타 문자를 일반 문자로 검색하기	
-	grep "^STR" [FILE] ___ 문자열 라인 처음 시작 패턴 검색하기	grep "^STR" [FILE]
- grep "$STR" [FILE]___ 문자열 라인 마지막 종료 패턴 검색하기	
