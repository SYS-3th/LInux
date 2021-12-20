# Shell
## 오늘 날짜를 저장하는 파일을 생성
- 저장위치 :/home/roro/date_log ,파일 이름 :Date_211210.txt
- 저장 위치에 해당하는 폴더,파일이 없으면 쉘 스크립트 통해서 생성되도록 처리

파일생성
```
vi test.sh

```
데이터 출력
```
!/bin/bash
date +"%Y-%m-%d %H:%M:%S"
```
타임존 추가
```
date +"%Y-%m-%d %H:%M:%S %z"
```
파일 날짜로 저장
```
touch backup_$(date +"%Y%m%d").txt

// 생성된 파일 이름
backup_20200701.txt
```
오늘날짜 디렉토리 만들기
```
mkdir $(date +"%Y-%m-%d")

// 출력 결과
2020-07-01/
```

