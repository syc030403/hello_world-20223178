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

1) -A : 모든 프로세스 출력.
2) a (BSD계열) : 터미널과 연관된 프로세스를 출력하는 옵션/ 보통 x 옵션과 연계하여 모든 프로세스를 출력할 때 사용
3) -a : 세션 리더(로그인 셀)을 제외하고 데몬 프로세스처럼 터미널에 종속되지 않은 모든 프로세스를 출력
4) -e : 커널 프로세스를 제외한 모든 프로세스를 출력
5) -f : 풀 포멧으로 보여줌/ 유닉스 스타일로 출력해주는 옵션으로 UID, PID, PPID등이 함께 표시됨
6) -l (sys V) : 긴 포맷으로 보여줌
7)  I (BSD계열) : 프로세스의 정보를 길게 보여주는 옵션으로 우선순위와 관련된 PRI와 NI값을 확인할 수 있음
8)  -o 값 : 출력 포멧을 지정하는 옵션으로 값으로는 pod, tty, time, cmd등을 지정할 수 있음
9)  -M : 64비트 프로세스들을 보여줌
10)  -m : 프로세스들 뿐만 아니라 커널 스레드들도 보여줌
11)  -p : 특정 PID를 지정할 때 사용
12)  -r : 현재 실행 중인 프로세서를 보여줌
13)  u (BSD계열) : 프로세스의 소유자를 기준으로 출력 (ps ax 만 하면 USER 기준의 정보가 안뜸, 따라서 대게 aux 이렇게 같이 써줌)
14)  -u : 특정 사용자의 프로세스 정보를 확인할 때 사용/ 사용자를 지정하지 않으면 현재 사용자를 기준으로 정보를 출력
15)  x (BSD계열) : 데몬 프로세스처럼 터미널에 종속되지 않는 프로세스를 출력/ 보통 a옵션과 결합하여 모든 프로세스를 출력할 때 사용
16)  -x : 로그인 상태에 있는 동안 아직 완료되지 않은 프로세서들을 보여줌
  
  16 - 1) 유닉스 시스템은 사용자가 로그아웃 한 후에도 임의의 프로세서가 계속 동작하게 할 수 있음. 그러면 그 프로세서는 자신을 실행시킨 셀이 없어도 계속 자신의 일을 수행하는데 이러한 프로세스는 일반적인 ps 명령으로 확인할 수 없음. 이 때 -x 옵션을 사용하면 자신의 터미널이 없는 프로세서들을 확인할 수 있음.
