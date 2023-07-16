# Ubuntu 노트북 덮개를 닫아도 대기모드에 진입하지 않게 설정하는 방법
1. `sudo vi /etc/systemd/logind.conf`: logind.conf 파일 편집 열기
2. `#HandleLidSwitch=suspend`의 주석을 제거하고, suspend 대신 ignore로 바꿔주기  
    ```
    HandleLidSwitch=ignore
    ```
3. `systemctl restart systemd-logind`: systemd-logind 서비스 재시작을 통해 해당 설정 실시간 반영하기