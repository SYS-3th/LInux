# Package Mabging

패키지 관리란 새로운 소프트웨어를 설치, 업데이트, 삭제하는 일을 말한다. 소프트웨어는 소스코드의 형태로 배포되는 경우와 바이너리 패키지 형태로 배포되는 경우가 있는데, 소스코드의 경우 보통 하나의 아카이브 파일(tar)로 묶은 후 압축하여 배포한다. 바이너리 패키지에는 응용 프로그램, 라이브러리 파일, 버전 정보나 의존성 등의 메타 정보 파일 등이 포함된다

 

패키지는 저장소(repository)에 저장되어 있으며, HTTP 혹은 FTP 서버를 통해 다운로드 할 수 있다. 하나의 패키지가 다른 패키지나 공유 라이브러리 등을 필요로 하는 관계를 패키지 간의 의존성(dependency)라고 부른다. 의존성을 해결하는 기능을 제공하는 것이 리눅스의 패키지 관리 시스템의 주요 역할이다.


## 패키지 

리눅스 배포판에 따라서 서로 다른 패키지 형식을 지원하는데 대부분 다음의 3가지 중 하나를 지원한다


- Debian 계열 (Debian, Ubuntu 등) : .deb 파일

- RedHat 계열 (RedHat, Fedora, CentOS) : .rpm 파일

- openSUSE 계열 : openSUSE를 위해 특별히 빌드된 .rpm 파일

Ubuntu에서는 /var/cache/apt/archives 디렉터리에 다양한 .deb 파일들이 보관되어 있다. 이러한 패키지를 관리하기 위해선 패키지 관리 도구를 사용하는데, 일반적으로 다음 두 유형의 패키지 관리 도구가 사용된다

 

- 저수준 툴(low-level tools) : 실제 패키지의 설치, 업데이트, 삭제 등을 수행

- 고수준 툴(high-level toos) : 의존성의 해결, 패키지 검색 등의 기능을 제공

 

아래 표는 리눅스 배포판 별로 저수툰/고수준 패키지 관리 도구를 나타내었다

![다운로드](https://user-images.githubusercontent.com/88940298/146100740-3081f1dd-91af-4881-b447-1e8f94e9fbb7.png)


## 각 패키지 관리 도구에 대해서 간단히 설명하면 다음과 같다

### dpkg

- Debian 기반의 리눅스에서 사용되는 저수준 패키지 관리자(low-level package manager)

- deb 패키지의 설치와 삭제를 담당

- 하지만 자동으로 패키지를 다운로드하거나 의존성을 해결해주지는 않음

### apt-get / apt-cache / apt

- Debian 기반의 리눅스에서 사용되는 고수준 패키지 관리자(high-level package manager)

- 패키지를 검색, 다운로드, 설치, 의존성 해결

- 최근의 Debian 기반의 리눅스 배포판에는 apt-get과 apt-cache 의 기능을 통합한 apt 명령이 설치되어 있다

### aptitude

- Debian 기반의 리눅스의 또 다른 high-level package manager

- apt-get 보다 좀 더 개선된 기능을 제공

## 사용 
### dpkg
```
$ dpkg --help
$ dpkg -k flashpluginnonfree_2.8.2+squeeze1_i386.deb	// 패키지의 설치
$ dpkg -l						// 설치된 패키지를 나열
$ dpkg -l apache2					// 설치되었는지 확인
$ dpkg -r flashpluginnonfree				// 설치된 패키지를 삭제
```

### apt-get / apt-cache의 경우 패키지 repository는 /etc/apt/sources.list 에 명시되어 있다

```
test@ubuntu:~$ sudo cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 18.04.2 LTS _Bionic Beaver_ - Release amd64 (20190210)]/ bionic main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
.
.
.
```
### /etc/apt/sources.list 파일에 명시된 패키지는 앞에서부터 순서대로 패키지 유형(deb 혹은 deb-src), 저장소 URL, Debian 버전 정보, 카테고리를 명시한다. 패키지 repository 리스트의 업데이트는 다음 명령을 통해 수행할 수 있다

```
$ sudo apt-get update
or
$ sudo apt update

```

다음 표는 리눅스 패키지 관리 도구를 사용하여 패키지를 관리하는 방법들을 정리해서 나타낸 것이다
![다운로드 (1)](https://user-images.githubusercontent.com/88940298/146101031-734b0bfe-ee7f-42dc-9c38-c8843fffddb3.png)

