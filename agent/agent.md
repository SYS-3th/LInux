# Wget

## 브라우저에서 다운로드 하는것 처럼 useragent 정보 내보내기

## 다운로드 가능한지 확인하기
## 재시도 횟수 지정하기
## 여러개의 파일 지정하기 
## ftp파일 저장히기

## 단일 파일 받기
다음의 예는 인터넷에서 단일 파일을 받아 현재 디렉토리에 저장하는 방법입니다.
```
$ wget DOWNLOAD-URL
```
다운로드 하는 동안 진행 경과와 함께 다음의 정보를 보여줍니다.

현재 몇 퍼센트 받았는지에 대한 정보 (2%)
현재까지 다운로드 받은 바이트 수 (112,550)
현재 다운로드 속도 (3.64KB/s)
다운로드 완료까지 남은 시간 (35s)
```
$ wget http://www.openss7.org/repos/tarballs/strx25-0.9.2.1.tar.bz2
HTTP request sent, awaiting response… 200 OK
Length: 3852374 (3.7M) [application/x-bzip2]
Saving to: ‘strx25-0.9.2.1.tar.bz2’
```
2% [=> ] 112,550 3.64KB/s in 35s

## 다른이름으로 저장하기
파일을 저장할 때 wget은 기본적으로 다운로드 경로의 마지막 슬래쉬(‘/’) 다음에 오는 단어를 파일이름으로 사용합니다. 그런데 이 방법으로는 올바른 파일이름이 아닌 이상한 이름을 뽑아내는 경우도 있습니다.
```
$ wget http://www.vim.org/scripts/download_script.php?src_id=7701
```
위의 경우 다운받은 파일 이름은 ‘download_script.php?src_id=7701’이 됩니다. 이런 상황을 해결하기 위해 ‘-O’ 옵션을 사용합니다.
```
$ wget -O taglist.zip http://www.vim.org/scripts/download_script.php?src_id=7701
```
## 다운로드 속도 지정
wget은 다운로드시 기본적으로 가능한 최대의 대역폭을 사용합니다. 그러나 대량의 파일을 받아야 한다면 사용하는 대역폭을 조절할 필요가 있습니다. ‘–limit-rate’ 옵션으로 다운로드 속도를 제한할 수 있습니다. 다음은 다운로드 속도를 200k로 제한하는 예입니다.
```
$ wget –limit-rate=200k DOWNLOAD-URL
```
## 이어받기
다운로드 도중 중단했을 경우 ‘-c’ 옵션으로 다시 시작할 수 있습니다.
```
$ wget -c DOWNLOAD-URL
```
이는 대용량 파일을 다운로드 받는 도중 멈추고 다른 작업을 해야했을 때 전체파일을 다시 받지 않고 이전에 받은 파일에 이어받을 수 있어서 유용합니다. 만일 ‘-c’ 옵션으로 이어받지 않고 이전에 다운로드 중이던 파일이 남아있으면 같은이름으로 다운도르 할 것이므로 새로운 받기에서는 파일이름 뒤에 ‘.1’이 추가됩니다. 여기서 ‘.1’이 이미 있으면 ‘.2’가 추가됩니다.

## 백그라운드에서 다운로드하기
대용량 파일을 받을 때 사용할 수있는 또다른 옵션입니다. 이는 다운로드 작업을 백그라운드로 돌리는데 ‘-b’ 옵션을 사용합니다.
```
$ wget -b http://www.openss7.org/repos/tarballs/strx25-0.9.2.1.tar.bz2
Continuing in background, pid 29401.
Output will be written to ‘wget-log’.
```
다운로드 상황은 wget-log에 모두 기록됩니다. 이 내용을 모니터링 하고싶으면 tail 명령어(tail -f wget-log)를 이용해 볼 수 있습니다.

브라우저에서 다운로드 하는 것 처럼 user-agent 정보 보내기
몇몇 웹사이트는 브라우저로 다운로드하지 않는다고 판단될 경우 다운로드를 허가하지 않는 경우가 있습니다. 이 때 ‘–user-agent’ 옵션으로 정보를 함께 보낼 수 있습니다.
```
$ wget –user-agent=”Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.3) Gecko/2008092416 Firefox/3.0.3″ DOWNLOAD-URL
```
## 다운로드 가능한지 확인하기
특정 시간에 다운로드 일정이 잡혀있을 때, 원격지에 파일이 존재하는지 아닌지 확인을 해봐야 합니다. 이 때 ‘–spider’ 옵션을 사용하여 링크가 올바른지 확인합니다.

### URL이 올바를 경우
```
$ wget –spider http://www.openss7.org/repos/tarballs/strx25-0.9.2.1.tar.bz2
Spider mode enabled. Check if remote file exists.
HTTP request sent, awaiting response… 200 OK
Length: 3852374 (3.7M) [application/x-bzip2]
Remote file exists.
```
### 에러가 있을 경우
```
$ wget –spider http://www.openss7.org/repos/tarballs/strx25
Spider mode enabled. Check if remote file exists.
HTTP request sent, awaiting response… 404 Not Found
Remote file does not exist — broken link!!!
```
## 재시도 횟수 지정하기
인터넷 연결에 문제가 있을 경우나 파일 다운로드 실패가 일어날 경우 기본 재시도 횟수는 20 입니다. 하지만 더 오래 시도해볼 필요가 있을 때 ‘–tries’ 옵션으로 재시도 횟수를 조정할 수 있습니다.
```
$ wget –tries=75 DOWNLOAD-URL
```
## 여러개의 파일 다운로드하기
여러 파일을 다운로드 하려면 다운로드 하려는 여러 링크를 써놓은 파일(엔터로 구분)을 만들고 ‘-i’ 옵션을 통해 작업을 진행합니다.
```
$ wget -i FILE-WHICH-HAS-URLS
```


간혹 wget으로 여러 파일을 받으려고할 때가 있다. 그럴 때 wget을 이용해서 다음과 같이 파일을 다운로드 받을 수 있다.


```
wget -nd http://xxx.com/경로/파일명{반복 리스트}.확장자
```


가령, 예를 들어서 인간 참조 지놈의 모든 염색체 서열을 NCBI로 부터 다운로드 받는다고 하자.



그럴 때 다음과 같이 할 수 있다.


```
wget -nd ftp://ftp.ncbi.nlm.nih.gov/genomes/H_sapiens/Assembled_chromosomes/seq/hs_alt_HuRef_chr{ 1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,X,Y }.fa.gz

```
```
wget ftp://ftp.ncbi.nlm.nih.gov/genomes/H_sapiens/Assembled_chromosomes/seq/hs_alt_HuRef_unplaced.fa.gz

```

다음과 같이 하면, 순서대로 hs_alt_HuRef_chr1.fa.gz 부터 hs_alt_HuRef_chrY.fa.gz 까지와 hs_alt_HuRef_unplaced.fa.gz

의 파일을 순서대로 다운로드 받게 된다.



주의할 점은 실제 명령어에서는 {(왼쪽 중괄호)와 1, Y와 }(오른쪽 중괄호) 사이에는 공백이 없으나 티스토리 블로그에서 잘못 표기되기 때문에 공백을 추가했다.

