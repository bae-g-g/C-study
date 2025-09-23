# Function:  Synchronous vs Asynchronous + Blocking vs Non-Blocking

# **Function:**
# **Synchronous vs Asynchronous**
# **Blocking vs Non-Blocking**

## **① KERNEL Definition 커널 정의**
[https://en.wikipedia.org/wiki/Operating\_system#Kernel](https://en.wikipedia.org/wiki/Operating_system#Kernel)

*   OS 운영체제 구성중 Computer 내부실행을 담당하는 핵심 Software

ⓐ Hardware 자원을 자원(CPU/Memory)이 필요한 Process에 배분

\= Programme 실행에 필요한 CPU 동작할 수 있는 시간 + Memory 용량 배분

ⓐ1 Memory Control 메모리 제어

ⓐ2 Hardware Control 하드웨어 제어

...

ⓑ Process Control 프로세스 제어

ⓑ1 Task Manager 작업 관리

ⓑ2 Thread Manage/Execution 쓰레드 관리/실행

...

ⓒ Hardware에 Input/Output

파일 읽기/쓰기 by System Call (= KERNEL의 Functions)

*   OS 운영체제 가장 아래 계층에서 작동

現 OS 운영체제는 커널 위에 여러가지 소프트웨어 계층을 적층함

![](https://t9003081320.p.clickup-attachments.com/t9003081320/889e1645-f426-41b2-a1b5-8ed6219fb1dc/Picture1.png)

∴ 커널 파손 ➝ OS 운영체제 작동하지 않음
∴ 커널 오작동(정지) ➝ OS 운영체제 정지 (KERNEL Panic 커널 패닉)
⟹ 현재는 Beta Test Version에서만 접할수 있음

*   커널은 STACK/HEAP Memory 를 가지지 않음
xcpt)
ⓐ 사용자 Programme이 System Call을 통해서 간접적으로 KERNEL Function 커널 함수를 호출
➝ System Call (= KERNEL의 Functions)
ⓑ 커널 공간에 KERNEL Functions Execution 커널 함수 실행을 위한 STACK이 "임시"로 생성
ⓒ 이 STACK은 커널이 직접관리하는 STACK이 아니라 커널 함수 완료시 해제되는 "임시" STACK
ⓒ1 CPU는 現 실행에 필요한 DATA를 Register에 저장
ⓒ2 우선순위 높은 실행이 Load 되었을때,
ⓒ1 실행을 Register에서 "임시" STACK 으로 이동
ⓒ3 우선순위 높은 실행 완료후,
ⓒ1 실행을 "임시" STACK 에서 Register로 가져오고 "임시" STACK 해제
∴ 커널 자체가 STACK을 가진다고 보기 어려움

*   커널은 OS 운영체제의 정체성을 결정

e.g. Linux KERNEL-Used 리눅스 커널 사용 ➝ Fedora 페도라, Ubuntu 우분투, etc.

## **② KERNEL Type 커널 유형**

*   **Monolithic KERNEL 단일형 커널**

e.g.

UNIX-Family 유닉스 계통

[https://namu.wiki/w/UNIX](https://namu.wiki/w/UNIX)

. 현대적 컴퓨터 운영 체제의 원형

. 本 멀틱스 운영체제(Made in MIT)에 기반한 다중 사용자용 서버운영 체제

. 現 개인용 데스크탑 or 임베디드용 운영체제 전신

. Genetic Unix 유전적 , Trademark Unix 상표, Functional Unix 기능적

LINUX KERNEL

. Genetic Unix 유전적 (X), Trademark Unix 상표 (X), Functional Unix 기능적 (O)

MS-DOS 및 그에 기반한 Windows 9x(윈도우 95, 98, ME)

Mac OS 8.6 이하 Version

![](https://t9003081320.p.clickup-attachments.com/t9003081320/12393ea1-4a03-40bb-b693-aee181401b0d/image.png)

리눅스 커널 구조도

1개의 커널이 OS 운영체제에서 일어나는 All Tasks 처리
e.g. 입/출력, 네트워크, 시스템콜, 주변장치관리, etc. 처리
ⓐ 속도 빠름
ⓑ 설계 편리
ⓒ 안정성/보안성 문제 잠재
ⓓ 커널의 크기 방대
∴ 사장되고 있음
⟹ KERNEL Binary에 어떠한 기능이 포함되어 있지 않더라도 커널에 기능 추가 등의
Micro KERNEL 마이크로 커널의 특성을 포함한 모듈방식 채택하여 개선
e.g. Linux의 DKMS, FreeBSD의 kld, NetBSD

*   **Micro KERNEL 마이크로 커널**
e.g.
AmigaOS
Amoeba
Mach
Minix
L4
QNX
GNU Hurd
지르콘
심비안

![](https://t9003081320.p.clickup-attachments.com/t9003081320/c5136fbc-be25-4654-be09-6d3beaccbf5b/image.png)

KERNEL = Server
Monolithic KERNEL 단일형 커널이 처리하던 Some Tasks 제외
e.g. 시스템콜, 주변장치관리, etc. 제외
User Space = Client
➝ Client가 어떤 실행이 필요하면 Server에 요청하는 방식
➝ KERNEL이 응용 프로그램 계층으로 제공하는 방식(나누어져 작동하는 방식) 으로 처리
![](https://t9003081320.p.clickup-attachments.com/t9003081320/a0c8be8f-7058-460f-a685-efd1a68f5bf5/Picture1.png)
Core Software = KERNEL (시스템콜, 주변장치관리, etc.) = Server
Software #1 ~ #n = User Space (Filesystem, Netwerk Stack, etc.) = Client

ⓐ 안정성/보안성 높임
ⓑ 커널의 크기 축소
ⓒ 성능 저하

*   **Hybrid KERNEL 혼합형 커널**

e.g.

NT 커널

(Windows NT 3.1, NT 3.5, NT 3.51, NT 4.0, 2000, XP, Vista, 7, 8, 8.1, 10, 11)

(Windows Server 2003, 2003 R2, 2008, 2008 R2, 2012, 2012 R2, 2016, 2019)

XNU - Darwin과 이에 기반을 둔 Mac OS, iOS가 XNU

Ref) XNU 커널 = Mach 커널 + BSD 단일형 커널

⒜ Mach 커널 (Made in Carnegie Mellon UNI)

분산 및 병렬 연산 지원을 목표로 개발

⒝ BSD (Made in UC Berkeley)

UNIX 계열

개발언어 C

FreeBSD - 높은 성능

NetBSD - 이식성 (비 x86, AMD64에서 유용함 ➝ 다양한 CPU 제조사와 연동)

OpenBSD - 보안

DragonFly BSD - 높은 확장성

Ref) LINUX와 차이점

. LINUX는 LINUX Foundation에서 관리 vs BSD는 관리자 無

. LINUX = KERNEL vs BSD = OS 운영체제 전체

커널만 개발/배포 데스크탑 환경 및 응용 소프트웨어 포함 개발/배포

≒ 기능有 GUI無 ≒ 기능有 GUI有 (e.g. Windows, Mac OS)

Terminal Window만 있음

BeOS

하이쿠

Plan 9

![](https://t9003081320.p.clickup-attachments.com/t9003081320/dd07db76-4917-4552-a0b4-1dcc16b15b48/image.png)
윈도우 NT 계열 커널 구조도
ⓐ Hardware Abstraction Layer (HAL) = Hardware의 일부분을 Virtual Hardware(Software)로 할당
HAL = Virtual Hardware(Software)로 할당시 섹션 구분 주소값을 정의
ⓑ Monolithic KERNEL Mode - Micro KERNEL Mode Automatic Transition Operation

ⓒ Monolithic KERNEL 단일형 커널 장점 + Micro KERNEL 마이크로 커널 (성능저하 단점해결)
➝ 성능이 요구되는 OS 운영체제 Service를 커널에 포함

*   **Exo KERNEL 엑소 커널**

[https://en.wikipedia.org/wiki/Exokernel](https://en.wikipedia.org/wiki/Exokernel)

![](https://t9003081320.p.clickup-attachments.com/t9003081320/7be3a5d5-90c9-4192-b490-7fb023fabb3a/image.png)

ⓐ 다른 방식의 커널은 아님

ⓑ 다른 커널에 보너스로 구조화 형태로 들어감

ⓒ Programme에 Hardware를 통해 직접 제어할수 있는 선택권 줌

ⓓ 다른 커널이 존재하고, 사용자는 User Space만 사용하며,

사용자가 Exo KERNEL을 통해서 Hardware에 직접 접근 가능하게 함

*   **Nano KERNEL 나노 커널**

ⓐ 시스템이 작동하는 데 필요한 최소한의 서비스를 제공하는 운영 체제 아키텍처

ⓑ 기본적인 컴퓨터 작동을 관리하고 시스템의 일부가 서로 대화할 수 있도록 하는 등

가장 필요한 작업만 수행

ⓒ 더 복잡한 작업은 운영 체제의 다른 구성 요소에 위임

ⓓ 결과적으로 실질적 모든 서비스를 책임짐 = 최소한의 기본/핵심 수행은 가능

## **③ KERNEL Programming 커널 프로그래밍**

커널의 동작(커널을 통해서 사용자가 원하는 프로그램 사용 가능)을 위해 프로그래밍하는 것
*   File System & Partian Table 파일 시스템 및 파티션 테이블

e.g 디스크조각모음크조각모음

*   Device Driver 디바이스 드라이버

e.g. Input/Output Device Driver 입출력 장치 드라이버

⟹ Touch Screen, Mouse, Keyboard, Sound Card, Graphic Card

NVIDIA Graphic Card를 사용할 수 있도록 KERNEL에 Programming 해두는 것

*   Network API 네트워크 API

e.g. TCP/IP Protocol Stack TCP/IP 프로토콜 스택

Wireless Communication Device 무선 통신 기기 스텍

Ref) API

[https://aws.amazon.com/ko/what-is/api/](https://aws.amazon.com/ko/what-is/api/)

[https://www.ibm.com/kr-ko/topics/api](https://www.ibm.com/kr-ko/topics/api)

## **④ KERNEL Working Structure 커널 동작 구조**

*   Synchronous 동기

순서대로 하나씩 실행

한번에 하나씩 실행

*   Asynchronous 비동기

동시에 여러가지 실행

한번에 여러가지 실행

Ref) 순차적 실행 위해 콜백 함수 사용

*   Blocking 블로킹

완료후 다음 동작 실행

완료전 까지 다음 동작 실행 불가능

E.g.) C 언어

*   Non-Blocking 논블로킹

완료전 다음 동작 실행

완료와 상관없이 다음 동작 실행 가능

![](https://t9003081320.p.clickup-attachments.com/t9003081320/d2611958-713b-4ff0-b572-4f8cf02d5456/image.png)

*   Synchronous 동기 + Blocking 블로킹

Read/Write (어플리케이션이 커널에 Read or Write 시스템콜 요청)

파일 1개를 Read or Write 실행 완료후 ➝ 다음 동작 실행

파일 1개를 Read or Write 실행 완료후 ➝ 다음 동작 실행

. 완료시 까지 어플리케이션이 멈춰 있음

. 커널이 제어권을 어플리케이션에 돌려줄때 까지 어플리케이션이 멈춰 있음

. 어플리케이션이 제어권을 가지고 있지않음

*   Synchronous 동기 + Non-Blocking 논블로킹

Read/Write (어플리케이션이 Non-Blocking 설정된 커널에 Read or Write 시스템콜 요청)

파일 1개를 Read or Write 실행 완료전 ➝ 다음 동작 실행

파일 1개를 Read or Write 실행 완료전 ➝ 다음 동작 실행

. 완료전 까지 어플리케이션이 멈춰 있지않음

. 커널이 제어권을 어플리케이션에 돌려주어 어플리케이션이 멈춰 있지 않음

. 어플리케이션이 제어권을 가지고 있음

. 커널이 제어권을 가지고 있지 않음

※ Indeed, 어플리케이션이 커널에 제어권을 잠시 넘겨주고 바로 돌려받음|

※ Indeed, 동기 + 논블로킹 = 동기 + 블로킹의 변형 = 동기 + 짧은 주기의 블로킹

*   Asynchronous 비동기 + Blocking 블로킹

Input/Output (어플리케이션이 커널에 Input or Output 시스템콜 요청)

파일 n개에 Data를 Input or Output 실행을 n개 파일 전체에 완료후 ➝ 다음 동작 실행

파일 n개에 Data를 Input or Output 실행을 n개 파일 전체에 완료후 ➝ 다음 동작 실행

(실행 n개) (동작 1개)

. 완료시 까지 어플리케이션이 멈춰 있음

. 커널이 제어권을 어플리케이션에 돌려줄때 까지 어플리케이션이 멈춰 있음

. 어플리케이션이 제어권을 가지고 있지않음

*   Asynchronous 비동기 + Non-Blocking 논블로킹

Input/Output (어플리케이션이 Non-Blocking 설정된 커널에 Input or Output 시스템콜 요청)

파일 n개에 Data를 Input or Output 실행을 n개 파일 각각에 완료전 ➝ 다음 동작 실행

파일 n개에 Data를 Input or Output 실행을 n개 파일 각각에 완료전 ➝ 다음 동작 실행

(실행 n개) (동작 n개)

. 완료전 까지 어플리케이션이 멈춰 있지않음

. 커널이 제어권을 어플리케이션에 돌려주어 어플리케이션이 멈춰 있지 않음

. 어플리케이션이 제어권을 가지고 있음

. 커널이 제어권을 가지고 있지 않음

※ Indeed, 어플리케이션이 커널에 제어권을 잠시 넘겨주고 바로 돌려받음

* * *

① Synchronous 동기 + Blocking 블로킹 ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-6778](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-6778))

② Synchronous 동기 + Non-Blocking 논블로킹 ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-6798](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-6798))

③ Asynchronous 비동기 + Blocking 블로킹 ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-6818](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-6818))

④ Asynchronous 비동기 + Non-Blocking 논블로킹 ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-6858](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-6858))

* * *

※ Handle ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-7138](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-7138))