# 리눅스 명령어 조사



### 1. top

+ 시스템의 상태를 전반적으로 가장 빠르게 파악 가능(CPU, Memory, Process)
+ 옵션 없이 입력하면 interval 간격(기본 3초)으로 화면을 갱신하며 정보를 보여줌


+ top 실행 전 옵션

 1) 순간의 정보를 확인하려면 -b 옵션 추가(batch 모드)
 2) -n : top 실행 주기 설정(반복 횟수)


+ top 실행 후 명령어

1) shift + p : CPU 사용률 내림차순
2) shit + m : 메모리 사용률 내림차순
3) shift + t : 프로세스가 돌아가고 있는 시간 순
4) k : kill. k 입력 후 PID 번호 작성. signal은 9
5) f : sort field 선택 화면 -> q 누르면 RES순으로 정렬
6) a : 메모리 사용량에 따라 정렬
7) b : Batch 모드로 작동
8) 1 : CPU Core별로 사용량 보여줌

---------------------

### 2. ps

+ 현재 실행중인 프로세스 목록과 상태를 보여줌
+ 전통적인 유닉스인 System V, BSD, GNU에 따라 결과가 다르게 나타나고 표기법에도 차이를 보임
+ 옵션 사용시 System V 계열은 dash(-)를 사용하고 BSD 계열은 - 를 사용하지 않음
+ GNU에서의 욥션 표기는 두 개의 - 를 사용
+ ###### 따라서 원하는 프로세스의 상태를 출력하려면 정확한 옵션 사용이 중요


+ ps 옵션

1) **-A** : 모든 프로세스 출력.
2) **a** (BSD계열) : 터미널과 연관된 프로세스를 출력하는 옵션/ 보통 x 옵션과 연계하여 모든 프로세스를 출력할 때 사용
3) **-a** : 세션 리더(로그인 셀)을 제외하고 데몬 프로세스처럼 터미널에 종속되지 않은 모든 프로세스를 출력
4) **-e** : 커널 프로세스를 제외한 모든 프로세스를 출력
5) **-f** : 풀 포멧으로 보여줌/ 유닉스 스타일로 출력해주는 옵션으로 UID, PID, PPID등이 함께 표시됨
6) **-l** (sys V) : 긴 포맷으로 보여줌
7)  **I** (BSD계열) : 프로세스의 정보를 길게 보여주는 옵션으로 우선순위와 관련된 PRI와 NI값을 확인할 수 있음
8)  **-o** 값 : 출력 포멧을 지정하는 옵션으로 값으로는 pod, tty, time, cmd등을 지정할 수 있음
9)  **-M** : 64비트 프로세스들을 보여줌
10)  **-m** : 프로세스들 뿐만 아니라 커널 스레드들도 보여줌
11)  **-p** : 특정 PID를 지정할 때 사용
12)  **-r** : 현재 실행 중인 프로세서를 보여줌
13)  **u** (BSD계열) : 프로세스의 소유자를 기준으로 출력 (ps ax 만 하면 USER 기준의 정보가 안뜸, 따라서 대게 aux 이렇게 같이 써줌)
14)  **-u** : 특정 사용자의 프로세스 정보를 확인할 때 사용/ 사용자를 지정하지 않으면 현재 사용자를 기준으로 정보를 출력
15)  **8x** (BSD계열) : 데몬 프로세스처럼 터미널에 종속되지 않는 프로세스를 출력/ 보통 a옵션과 결합하여 모든 프로세스를 출력할 때 사용
16)  **-x** : 로그인 상태에 있는 동안 아직 완료되지 않은 프로세서들을 보여줌
  
  16 - 1) 유닉스 시스템은 사용자가 로그아웃 한 후에도 임의의 프로세서가 계속 동작하게 할 수 있음. 그러면 그 프로세서는 자신을 실행시킨 셀이 없어도 계속 자신의 일을 수행하는데 이러한 프로세스는 일반적인 ps 명령으로 확인할 수 없음. 이 때 -x 옵션을 사용하면 자신의 터미널이 없는 프로세서들을 확인할 수 있음.




+ **ps 항목**

|항목|설명|
|:-------:|:--------:|
|USER|BSD계열에서 나타나는 항목으로 프로세스 소유자의 이름|
|UID|System V 계열에서 나타나는 항목으로 프로세스 소유자의 이름|
|PID|프로세스의 식별번호|
|PPID|부모 프로세스 ID|
|%CPU|CPU 사용 비율의 추정치 (BSD)|
|%MEM|메모리의 사용비율의 추정치 (BSD)|
|VSZ|K단위 또는 페이지 단위의 가상메모리 사용량|
|RSS|실제 메모리 사용량 (Resident Set Size)|
|TTY|프로세스와 연결된 터미널|
|S, STAT|현재 프로세스의 상태 코드 (S: Sys V, STAT: BSS)|
|TIME|총 CPU 사용 시간|
|COMMAND|프로세스의 실행 명령행|
|STIME|프로세스가 시작된 시간 혹은 날짜|
|C, CP|짧은 기간 동안의 CPU 사용율 (C: Sys V, CP: BSD)|
|F|프로세스의 플래그|
|PRI|실제 실행 우선순위|
|NI|nice 우선순위 번호|


-------------------------

### 3. jobs

+ 작업의 상태를 표시하는 명령어
+ 현재 쉘 세션에서 실행시킨 백그라운드 작업의 목록이 출력되며, 각 작업에는 번호가 붙어 있어 kill 명령어 뒤에 '%번호' 등으로 사용할 수 있음


+ **jobs 상태**

|상태|설명|
|:-----:|:------:|
|Running|작업이 계속 진행중|
|Done|작업이 완료되어 0을 반환|
|Done(code)|작업이 종료되었으며 0이 아닌 코드를 반환|
|Stopped|작업이 일시 중단|
|Stopped(SIGTSTP)|SIGTSTP 시그널이 작업을 일시 중단|
|stopped(SIGSTOP)|SIGSTOP 시그널이 작업을 일시 중단|
|Stopped(SIGTTIN)|SIGTTIN 시그널이 작업을 일시 중단|
|Stopped(SIGTTOU)|SIGTTOU 시그널이 작업을 일시 중단|


+ **job 옵션**

|옵션|설명|
|:---:|:---:|
|-l|프로세스 그룹ID를 state필드 앞에 출력|
|-n|프로세스 그룹 중에 대표 프로세스 ID를 출력|
|-p|각 프로세스 ID에 대해 한 행씩 출력|
|command|지정한 명령어를 실행|


-----------------------------

### 4. kill

+ 프로세스를 죽일 떄 사용
+ 내부적으로는 프로세스에 시그널을 보내 원하는 작업을 하게 하는 명령어

+ **사용 구문** : $ kill [option]<pid>[...]

+ **프로세스 죽이는 방법**
1) 죽이려는 프로세스의 pid를 얻은 다음 kill 명령어의 인자로 넘기면 됨
2) $ kill[pid]

+ **사용자 지정 시그널 전송 방법**
1) kill 명령어의 default 시그널은 TERM(15), 하지만 -s 명령으로 다른 시그널을 보낼 수 있음
2) $ kill -s[signal][pid]
3) 예를 들어 프로ㅓ세스가 TERM(15)시그널에 응다밧ㅎ지 않으면 다음 명령어 처럼 KILL(9)를 사용해 강제로 죽일 수 있음
4)$ kill -s KILL[pid]

+ 사용 가능한 시그널 목록은 -ㅣ 명령어를 통해 지원하는 시그널의 목록을 확인 할 수 있음
+ $ kill -l
 
 ------------------------------
 
 ### 리눅스 매크로 사용법
 
 + 매크로 란?
 1) 특정한 움직임 또는 입력을 키에 자장함으로써 단순하면서 반복되는 동작을 쉽고 빠르게 해주는 것
 
 + vi 에서 매크로는 명령어 모드에서 q + 알파벳을 눌러 특정 알파벳에 매크로를 저장할 수 있음
 
 + **매크로 사용 순서**
 
 |단계|입력|설명|
 |:---:|:---:|:---:|
 |1|q + a|a키에 recording 시작|
 |2|내가 원하는 동작|리눅스 명령어|
 |3|q|recording 종료|
 |4|@a|1회 실행|
 |4 - 1|@@|방금 실행한 매크로 실행|
 |4 - 2|10@a|매크로 10회 실행|

+ 응용 (숫자 증가)

 |단계|설명|
 |:---:|:---:|
 |1| 1 숫자 입력|
 |2| 매크로 시작|
 |3| 1 숫자를 복사해서 다음줄에 붙여넣기|
 |4| 두번째줄 1에서 커서를 올리고 Ctrl + a(숫자 증가)|
 |5| 매크로 종료|
 
+ 숫자 증가 매크로 핵심 키
 1) Ctrl + a (숫자 증가)
 2) Ctrl + x (숫자 감소)
