# top, ps, jobs, kill 명령어에 대해 알아보자
**20243055 이민성**

# top
현재 OS의 상태를 나타낸다. 

메모리 사용량, CPU 사용량 등의 상황을 실시간에 근접하여 보여준다.  

위에는 전체의 요약이 있으며 아래에는 각 프로세스마다 구체적인 내용을 포함하고 있다.

![image](https://github.com/LateButRight/OSS_Introduction/assets/166789383/a66b12b9-0c57-44e4-8839-e520cb4c3bd7)

## 상단: 요약 영역
전체 프로세스가 OS에서 리소스를 얼마나 차지하고 있는지를 확인하는 명령어이다.

+ 시간, 유저
  + 시스템 현재 시간
  + OS의 구동 시간
  + 현재 접속 중인 유저 세션 수
+ 로드 에버리지(Loat Average)
  + 1분
  + 5분
  + 15분
+ 태스크(Tasks)
  + total: 전체 프로세스의 수
  + running: running 상태의 프로세스의 수
  + sleeping: 대기 상태의 프로세스의 수
  + stopped: 종료된 프로세스의 수
  + zombie: 좀비 상태의 프로세스의 수
+ CPU: CPU의 사용 비율을 보여줌
  + us: 유저 영역에서의 사용률
  + sy: 커널 영역에서의 사용률
  + ni: 우선순위 설정에서의 사용률
  + id: 사용하고 있지 않는 비율
  + wa: IO가 완료될 때까지 기다리고 있는 비율
  + hi: 하드웨어 인터럽트에 사용되는 비율
  + si: 소프트웨어 인터럽트에 사용되는 비율
  + st: CPU를 VM에서 사용하여 대기하는 비율
+ 메모리: mem은 **RAM**의 메모리 영역, swap은 **디스크**의 메모리 영역
  + total: 총 메모리 양
  + free: 사용 가능한 메모리 양
  + used: 사용 중인 메모리 양

## 하단: 디테일 영역
|항목|역할|
|:---|---:|
|PID|프로세스 ID를 나타냄. 프로세스 구분을 위한 고유한 값|
|USER|실행/효과를 받는 USER의 이름|
|PR|커널에 의해서 스케줄링되는 우선순위|
|NI|PR에 영향을 주는 값|
|VIRT|프로세스가 소비하고 있는 총 메모리|
|RES|RAM에서 사용 중인 메모리의 크기|
|SHR|다른 프로세스와의 공유 메모리|
|S|프로세스의 현재 상태|
|%MEM|RAM에서 RES가 차지하는 비율|
|TIME+|프로세스가 사용한 토탈 CPU|
|COMMAND|해당 프로세스를 실행한 커맨드|


# ps
현재 실행 중인 프로세스의 목록을 보는 명령어이다.

## 옵션
+ -e: 실행 중인 모든 프로세스의 정보 출력
+ -f: 프로세스에 대한 자세한 정보 출력
  ![image](https://github.com/LateButRight/OSS_Introduction/assets/166789383/82a4c45e-fc11-4f56-b6bf-6f6163ca9e34)
  + UID: 프로세스를 실행한 사용자 ID
  + PID: 프로세스 번호
  + PPID: 부모 프로세스 번호
  + C: CPU 사용량
  + STIME: 프로세스의 시작 시간
  + TTY: 프로세스가 실행된 터미널의 종류와 번호
  + TIME: 프로세스 실행 시간
  + CMD: 사용한 명령어
+ -u [사용자 이름]: 특정 사용자에 대한 모든 프로세스의 정보 출력
+ -p pid: pid로 지정한 프로세스의 정보 출력
+ u: 프로세스 소유자의 이름, CPU 사용량, 메모리 사용량 등 상세 정보 출력
+ a: 터미널에서 실행한 프로세스의 정보 출력
+ x: 실행 중인 모든 프로세스의 정보 출력
