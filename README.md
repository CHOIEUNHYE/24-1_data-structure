# 24-1_data-structure

## Windows11에서 Ubuntu 환경 세팅

> 1. start menu -> Windows기능켜기/끄기 -> "Linux용 Windows 하위 시스템" 체크 -> Restart
> 2. start menu -> Microsoft Store -> Search for "Ubuntu" -> Ubuntu 20.04 LTS 설치
> 3. start menu -> Search for "Ubunt" -> 실행 -> username과 password 세팅 -> 환경 세팅 완료 !

## Ubuntu 사용하기

### 1. 현재 디렉토리 확인
```bash
pwd
```

### 2. 현재 디렉토리의 존재하는 파일,폴더 리스트 확인
```bash
ls
```

### 3. 새 파일 만들기, 수정하기
```bash
vi <filename>
```

### 4. 파일 옮기기
```bash
mv <filename> <target directory>
```
---

## Windows 파일을 Linux 서버로 보내기

## Ubuntu cmd에서 할 일
### 1. 저장소 업데이트 하기
```bash
sudo apt update
```
### 2. openssh-server 설치하기
```bash
sudo apt install openssh-server
```
### 3. ssh 실행하기
```bash
sudo service ssh start
```
### 4. ssh 실행 상태 확인하기
```bash
service ssh status

>>  * sshd is running
```
### 5. ssh 패스워드 접속 허용하기

```bash
sudo vim /etc/ssh/sshd_config
```
화면에 파일이 열리면 두 가지 항목을 수정해야한다. 수정 모드로 들어가기 위해서는 `i`를 눌러준다.
```
#PermitRootLogin prohibit-password -> PermitRootLogin yes
PasswordAuthentication no -> PasswordAuthentication yes
```
수정이 완료되면 `esc`를 누른후 `:wq`라고 입력한 뒤 `enter`하면 초기 cmd 화면으로 돌아온다
### 6. ssh 재실행 하기
```bash
sudo /etc/init.d/ssh restart
```
### 7. 리눅스 서버 IP 확인하기
```bash
hostname -I(대문자)

>> IP주소 출력됨
```
출력된 리눅스 서버 IP는 윈도우 cmd에서 리눅스로 접근할 때 사용할 것이므로 기억해두자

## Windows cmd에서 할 일
### 리눅스 서버로 보낼 파일이 있는 디렉토리로 이동
```bash
cd <target directory in windows>
```
### 파일을 리눅스 서버로 전송
```bash
scp <filename in windows> <linuxID>@<linuxIP>:/<target directory in linux>
```
정상적으로 입력했다면 password를 입력하라는 메세지가 뜰 것이다. password를 입력하면 파일이 리눅스 서버로 전송된다.
