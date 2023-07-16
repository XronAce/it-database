# SSH로 접속할 수 있는 서버 구축하기
## SSH 설치
1. `sudo apt-get update && sudo apt-get upgrade`: 최신 레포지토리 업데이트 및 설치된 프로그램 최신화
2. `sudo apt-get install ssh`: ssh 설치
3. `sudo vi /etc/ssh/sshd_config`: ssh 설정 수정 진입
4. 
    ```bash
    PermitRootLogin yes # root로 접속이 가능토록 함.
    ```
5. `sudo service ssh start`: SSH 서버 실행
6. `service ssh status`: SSH 실행 상태 확인  
  
위와 같이 구축하면 기본적으로 해당 서버의 ip주소와 내부 포트 22번에 ssh가 열려 있다.
## IP 및 포트 확인
- `ifconfig`: ip 및 네트워크 MAC 주소 등 확인
- `sudo netstat -ntlp | grep sshd`: sshd가 돌아가고 있는 네트워크의 ip 및 포트 정보 출력
  - 만약 netstat 설치가 안되어 있다면 `sudo apt-get install netstat`으로 설치 가능
## SSH 접속 방법
`ssh <유저명>@<접근 주소> -p <포트번호>`
## 외부망에서 ubuntu 서버를 접속할 수 있도록 설정하는 방법
1. 인터넷 배선과 공유기를 직접 연결한다. 중간에 간섭하는 공유기가 있을 경우 DDNS 구축이 불가능하다.
2. 공유기에서 DDNS 서버를 구축한다.
3. 공유기와 서버용 pc를 연결한다. 안정성을 위해 유선 연결을 하는 것을 권장하고, 고정 IP 할당을 하는 것이 좋다.
4. 공유기에서 포트 포워딩을 설정한다. 이는 DDNS를 통해 공유기로 지정된 포트로 접근했을 시, 서버용 pc의 내부 ssh 포트(22)로 연결해 주기 위함이다.
5. [SSH 접속 방법](#ssh-접속-방법)에 설명된 <접근 주소>에 DDNS 서버 주소를 기재하고, <포트 번호>에 서버용 pc의 내부 ssh 포트(22)를 기재하여 접속한다.
