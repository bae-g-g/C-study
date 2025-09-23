# Memory (Management + Structure + Operation)

## **Memory Management 메모리 관리**

#### **Concept 개념**
*   Computer Memory(RAM)에 적용된 "Resource Management"의 "일종"

"Resource Management"

Computer 환경/성능에 따른 실행 차이

➝ CPU 성능 제한, Network 속도 제한, Memory 용량 제한 발생

∴ Memory Management 要
*   가장 효율적인 형태의 Memory Management 방법

Programme 요청시 Memory 일부를 해당 Programme에 "할당"

Programme 종료시 해당 Memory를 "해제"

∴ "할당" ➝ "해제" ➝ "할당" ➝ "해제" ....... (반복) .......

E.g.)
Computer Memory(RAM)는 용량 제한이 有
Programme 실행시 사용할 Memory "할당"(e.g. 변수 선언)
↓ ("할당" & "해제" 과정 要)
Programme 종료시 해당 Memory "해제"(e.g. 함수의 지역변수 Life Cycle 종료)

Ref)
Computer Memory(RAM)는 "해제"되지 않는 Case
malloc 사용자지정 함수 Memory 할당(= 동적 Memory 할당)
↓ 함수 100번 실행시 malloc 변수 선언시 Memory 100개 "할당"
↓ free 사용자지정 함수 사용하여 Memory "해재" 要
※ auto, static 변수는 ("할당" ➝ "해제") 반복
Computer 처리 용이로 인해 동일 공간에 ("할당" ➝ "해제")할 확율 증가

#### **Purpose 목적**
*   여러 Programmes이 동시에 실행될 수 있도록 Memory(RAM) 제공할 것

Programmes 실행 자체를 위해서도 Memory "할당"함

E.g)

Chrome + VSCODE + .exe 파일 실행 서로 간의 Memory "할당" 간섭 방지

⇒ .exe 파일의 실행 Memory 공간을 확인해 보면 유사한 공간에서 실행

Cf)

.exe 파일 생성 ➝ Compile시 Hard Disk의 Storage에 "할당"

.exe 파일 실행 ➝ Run Time시 그대로 RAM에 복사("할당")하여 실행

Programme 시작시(Run Time 시작시) "할당"

↓ Programme 중 (Run Time 중) 유지

Programme 종료시 (Run Time 종료시)"해제"

*   각 Programme의 Resource를 보호할 것

E.g. #1) Board Unit

Arduino Timer에서 16 Bits TCNT는 1 Byte(8 Bits) 2개로 구성
Arduino가 2개중 1개를 처리할 때, 나머지 1개가 Update되면 안됨
1개를 사용할 때, 나머지 1개 Update 되지 않도록 제한

E.g. #2) Server Unit

Bank Account 잔액이 100만원 있음

2개의 Debit Card(Check Card)로 동시에 결재를 할 때

1개의 Card로 70만원, 나머지 1개의 Card로 50만원 결재 시도 한다면

70만원 + 50만원 = 120만원 ➝ 잔액 초과 발생하기 때문에

1개 Card 결재 작동후, 나머지 Card 결재 작동하도록 결재 Code Memory "할당"

*   System 사용자들을 위해 만족할 만한 수준의 성능을 제공할 것
*   Programme "사이"에 있는 Memory 공간을 "유지/공유"할 것
*   Programmer를 위해 Memory 공간의 Addressing(주소값 할당)을 투명하게 할 것

★ OS 운영 체제 이해 필요
간단한 운영체제는 Building할 수 있는 역량 보유 要 (Default 역량)
∴ OS 운영 체제 교과목 수강 권장

* * *

## **Memory Structure + Operation 메모리 구조 + 동작**

#### **Memory (RAM)**

![](https://t9003081320.p.clickup-attachments.com/t9003081320/a9682d41-6386-491b-a404-bbed50cbaef4/image.png)
![](https://t9003081320.p.clickup-attachments.com/t9003081320/419dd39c-f9de-427f-8672-f7b136425371/image.png)
※ ROM: Read Only Memory (Persist)
※ RAM: Random Access Memory (Volatile)
★ CODE, CONST, crt0 = Run Time시 변경불가 X ➝ RAM의 일정부분을 ROM으로 설정

* * *

下 영역 용어 ➝ 메모리 Memory = RAM
下 영역 내용 ➝ C언어

#### **CODE (TEXT) & DATA Sector**
*   Compile시(.exe 파일 생성시) Hard Disk Storage에 "할당"

\= Compile시(.exe 파일 생성시) "할당" 크기가 파악되어야 함

*   Run Time시 RAM에 복사(RAM에도 "할당")하여 "실행"
➝ 변경 불가한 Contents "할당"

#### Structure 구조
CODE (TEXT) Sector
Programmer가 작성한 Source Codes가 Assembly Language Form 으로 "할당" 영역
*   Compile시(.exe 파일 생성시) Hard Disk Storage에 "할당" ➝ 이후 Read Only 읽기만 가능

\= Compile시(.exe 파일 생성시) "할당" 크기가 파악되어야 함

*   Run Time시 RAM에 복사(= RAM에도 "할당" ➝ RAM의 일정부분을 ROM으로 설정)하여 실행
➝ 변경 불가한 Contents "할당"

+

무엇을 해야하는지에 대한 명령어가 작성된 부분
함수(C Language는 함수들의 집합)가 Compile되어 저장됨
![](https://t9003081320.p.clickup-attachments.com/t9003081320/ea12cfdb-0ab5-4892-9444-337d05125a02/image.png)
text 9956
*   Programmer가 작성한 Source Codes (C Language: 함수 집합)의 용량
*   사용자정의 함수 선언시 어떤 실행을 할지에 대하여 Assembly Language Form으로 "할당"
E.g.)
"Assembly Language Form 1010101 = Parameter 2개를 더하여 Return 해라"로 "할당"

DATA Sector
static 변수(static & global) "할당" 영역
*   Compile시(.exe 파일 생성시) Hard Disk Storage에 "할당"

\= Compile시(.exe 파일 생성시) "할당" 크기가 파악되어야 함

*   Run Time시 RAM에 복사(= RAM에도 "할당")하여 실행

+

Life Cycle: Memory 할당된 Code Block 시작 ~ Programme 종료 (Code Block 종료 X)
➝ Run Time 동안 Programme 실행중 계속 유지되는 공간

+

Initialised Data + Uninitialised Data
*   Initialised Data 초기화된 Data

.GVAR

static int A = 5;

*   Uninitialised Data 초기화되지 않은 Data

.BSS

static int A;

![](https://t9003081320.p.clickup-attachments.com/t9003081320/43fd2c06-a439-488f-9552-623eb46441d5/image.png)
data 2228 = .GVAR 공간
bss 2432 = .BSS 공간
dec 14616 = 10진법 용량 표기 (text 9956 + data 2228 + bss 2432 = dec 14616)
hex 3918 = 16진법 용량 표기
Ref)
.exe 파일 생성의 메모리크기를 메모리구조로 확인하는 방법
`size .\파일명`
*   size .\\temp.exe
*   . = 현재폴더
*   \\ = "의" "하위의"
*   .\\ = Window Explore에서 ￦ / Mac Finder에서 >

+

E.g.)
일반 변수 (int, float, char)
메모리 "할당" = 자료형 크기 "할당" (e.g. int, float = 4 Bytes, char = 1 Byte)
① `static int X = 5;`
초기화된 변수 (.GVAR)
➊ Compile시(.exe 파일 생성시) Hard Disk Storage에 "할당"
상태: X라는 이름의 메모리 4 Bytes ➝ "할당"
∴ Compile Error 발생 X
➋ Compile후(.exe 파일 생성후) Run Time시(.exe 파일 실행시)
RAM에 복사(= RAM에 "할당")하여 "실행"
상태: X라는 이름의 메모리 4 Bytes ➝ 복사(= "할당") ➝ 초기화값 5 "실행"
② `static int X;`
초기화되지 않은 변수 (.BSS)
➊ Compile시(.exe 파일 생성시) Hard Disk Storage에 "할당"
상태: X라는 이름의 메모리 4 Bytes ➝ "할당"
∴ Compile Error 발생 X
※ 초기화값 = 사실상 쓰레기값 초기화 되어 있음
➋ Compile후(.exe 파일 생성후) Run Time시(.exe 파일 실행시)
RAM에 메모리 "크기만" 전달(= 메모리크기"만" RAM에 "할당")
상태: "전달"된 X라는 이름의 메모리 4 Bytes ➝ "할당" ➝ 초기화값 0 "실행"
※ static 변수의 특성: 초기화하지 않으면 0으로 자동 초기화 실행이 Run Time시 실행됨

배열 변수
배열 메모리 "할당" = (배열 요소 갯수 \* 배열 요소 자료형 크기) "할당"
*   메인 함수 작성시 下 내용 해당 O
*   사용자정의 함수 작성시 매개변수 작성시 下 내용 해당 X

∵ 매개 변수 = register 변수

➝ static 변수 선언 불가

➝ 매개 변수 static 변수로 선언시 문법 검사 오류 발생

➝ Compile Error

∵

인수 ➝(초기화)➝ 매개 변수: 초기화 시 인수"값만" 매개 변수에 전달

1) auto 매개 변수 처리 방식

RAM에 인수 할당 ➝ CPU Register에 초기화 ➝ CPU Register에서 처리 ➝ 처리값 RAM에 전달

2) static 매개 변수 처리ㅜ 방식

CPU Register에 초기화 ➝ CPU Register에서 처리

∴

매개 변수 = register 변수

① `static int array [n];` (e.g. n = 5)
배열 요소 갯수 지정 O
➊ Compile시(.exe 파일 생성시) Hard Disk Storage에 "할당"
상태: (배열 요소 갯수 n \* 배열 요소 자료형 4 Bytes) = n \* 4 "할당" (e.g. 5 \* 4 = 20 Bytes)
∴ Compile Error 발생 X
➋ Compile후(.exe 파일 생성후) Run Time시(.exe 파일 실행시)
RAM에 복사(= RAM에도 "할당")하여 "실행"
상태: array라는 이름의 메모리 20 Bytes 복사(= "할당") ➝ "실행"
② `static int array [ ];`
배열 요소 갯수 지정 X
➊ Complie시(.exe 파일 생성시) Hard Disk Storage에 "할당" X
상태: 배열 요소 갯수 파악 X ➝ int 4 Bytes 메모리 몇개 "할당" ?!?!?!?!
∴ Compile Error 발생 O
➋ Complie X (.exe 파일 생성 X) ➝ Run Time X (.exe 파일 실행 X)

Ref) Static 특성
*   Global Variable 전역변수 (변수 앞에 static 선언 생략 → 기본값 static)

static duration + internal linkage

Code Block 범위"밖" 존재

메모리 RAM 관련

메모리박스 할당된 Code Block 시작 ~ Programme 종료

*   Static Variable 정적변수

static duration + no linkage

Code Block 범위"내" 존재

메모리 RAM 관련

메모리박스 할당된 Code Block 시작 ~ Programme 종료

#### Operation 동작
메모리 "할당" 고정 영역 O
"할당" / "해제" 영역 X
Ref)
Programme 종료되면, 4개 영역(CODE, DATA, HEAP, STACK) 모두 메모리(RAM)에서 "해제"
CODE 영역에서 Compile시 Hard Disk Storage에 "할당"(저장)된 .exe 파일은 "유지"

#### **HEAP & STACK Sector**
*   Complie후(.exe 파일 생성후) Run Time시(.exe 파일 실행시) "할당"

\= Compile시(.exe 파일 생성시) "할당" 크기가 파악될 필요 없음

\= Run Time시(.exe 파일 실행시) "할당" 크기가 파악 되면됨

*   RAM에 바로 "할당"
➝ 변경 가능한 Contents "할당"

#### Structure 구조
HEAP Sector
Programme 실행중(Run Time중 = .exe 파일 실행중) 사용자가 직접 메모리에 "할당" / "해제" 영역
*   Complie후(.exe 파일 생성후) Run Time시(.exe 파일 실행시) "할당"

\= Compile시(.exe 파일 생성시) "할당" 크기가 파악될 필요 없음

\= Run Time시(.exe 파일 실행시) "할당" 크기가 파악 되면됨

*   RAM에 바로 "할당"

+

"할당" malloc, calloc, realloc + "해제" free 함수 사용

+

Low Address ➝ High Address "할당"

+

HEAP Overflow
"할당"을 너무 많이하면 STACK Sector 침범 ➝ HEAP Overflow 발생
E.g.) HEAP Overflow 표시: return n으로 Programme 종료, n = random int (e.g. 정수 0)

STACK Sector
메인 함수 + 사용자정의 함수 "관련" 메모리 "할당" / "해제" 영역
*   Complie후(.exe 파일 생성후) Run Time시(.exe 파일 실행시) "할당"

\= Compile시(.exe 파일 생성시) "할당" 크기가 파악될 필요 없음

\= Run Time시(.exe 파일 실행시) "할당" 크기가 파악 되면됨

*   RAM에 바로 "할당"

+

Local Variable 지역변수, Parameter 매개변수, Return 반환값 등의 "할당" 영역
E.g.)
일반 변수 (int, float, char)
메모리 "할당" = 자료형 크기 "할당" (e.g. int, float = 4 Bytes, char = 1 Byte)
① `int X = 5;`
초기화된 변수
➊ Compile시(.exe 파일 생성시) Hard Disk Storage에 "할당" X
∴ Compile Error 발생 관련 X
➋ Compile후(.exe 파일 생성후) Run Time시(.exe 파일 실행시)
RAM에 바로 "할당"하여 "실행"
상태: X라는 이름의 메모리 4 Bytes ➝ "할당" ➝ 초기화값 5 "실행"
※ 선언 '동시' 초기화
Run Time시(.exe 파일 실행시) Code 실행하며 메모리크기 (+ 초기화 값) 확인 가능
∴ Run Time시 메모리 "할당" 가능
② `int X;`
초기화되지 않은 변수
➊ Compile시(.exe 파일 생성시) Hard Disk Storage에 "할당" X
∴ Compile Error 발생 관련 X
➋ Compile후(.exe 파일 생성후) Run Time시(.exe 파일 실행시)
RAM에 바로 "할당"하여 "실행"
상태: X라는 이름의 메모리 4 Bytes ➝ "할당" ➝ "실행"
※ 선언 '후' 초기화 (scanf %d %f %f)
Run Time시(.exe 파일 실행시) Code 실행하며 메모리크기 확인(자료형 크기: e.g. int) 가능
∴ Run Time시 메모리 "할당" 가능
Ref) 초기화값은 scanf 입력값으로 확인 가능

배열 변수
배열 메모리 "할당" = (배열 요소 갯수 \* 배열 요소 자료형 크기) "할당"
① `int array [n];` (e.g. n = 5)
배열 요소 갯수 지정 O ➝ 지역 변수 가능 O + 매개 변수 가능 O
➊ Compile시(.exe 파일 생성시) Hard Disk Storage에 "할당" X
∴ Compile Error 발생 관련 X
➋ Compile후(.exe 파일 생성후) Run Time시(.exe 파일 실행시)
RAM에 메모리 크기 복사(= RAM에 "할당")하여 "실행"
상태: array라는 이름의 메모리 20 Bytes "할당" ➝ "실행"
배열 요소 갯수 n \* 배열 요소 자료형 크기 4 Bytes = n \* 4 "할당" (e.g. 5 \* 4 = 20 Bytes)
∴ Run Time시 메모리 "할당" 가능

※ 초기화값 확인
1) 메인 함수내
Run Time시(.exe 파일 실행시) Code 실행하며 배열 요소 확인 가능
ⓐ 선언 동시 초기화
초기화 할 요소 직관적으로 확인 가능 (e.g. int X\[3\] = {1, 2, 3};)
ⓑ 선언 후 초기화
1) int, float
➝ Manually 배열 요소 위치(index) 지정 초기화 (e.g. X\[0\] = 1;)
➝ 반복문 사용
2) char
➝ scanf %s 사용
➝ 반복문 사용
∴ 초기화 요소값 확인 가능
2) 사용자정의 함수내
Run Time시(.exe 파일 실행시) Code 실행하며 배열 요소 확인 가능
\- 메인 함수의 인수
∴ 초기화 요소값 확인 가능

② `int array [ ];`
배열 요소 갯수 지정 X ➝ 지역 변수 가능 X + 매개 변수 가능 O

지역 변수 가능 X
➊ Compile시(.exe 파일 생성시) Hard Disk Storage에 "할당" X
➋ Compile후(.exe 파일 생성후) Run Time시(.exe 파일 실행시)
RAM에 메모리 크기 "할당"(= RAM에 "할당")하여 "실행"
Run Time 시 할당되지만, Complie 과정에서 문법 검사 통과 X
➝ Run Time시 Memory 할당 크기를 정확하게 하기위해서, Compile시 배열 크기 파악 필요 O
➝ 배열 크기 = 0 (e.g., int X\[0\];) 일지라도, 배열 크기 파악되기 때문에, Compile Error 발생 X

※ 메모리 크기 "할당"
1) 메인 함수내
ⓐ 선언 동시 초기화
e.g. int X\[ \] = {1, 2, 3};
초기화 할 요소 갯수 직관적으로 확인 가능 ➝ 적어도 배열크기 3개 "할당"
ⓑ 선언 후 초기화
e.g. int X\[ \];
초기화 할 요소 갯수 파악 불가 ➝ 배열크기 "할당" 불가 ➝ Complie Error
2) 사용자정의 함수내
ⓐ 선언 동시 초기화
e.g. int X\[ \] = {1, 2, 3};
초기화 할 요소 갯수 직관적으로 확인 가능 ➝ 적어도 배열크기 3개 "할당"
ⓑ 선언 후 초기화
e.g. int X\[ \];
초기화 할 요소 갯수 파악 불가 ➝ 배열크기 "할당" 불가 ➝ Complie Error

매개 변수 가능 O
➊ 인수 ➝(초기화)➝ 매개 변수: 초기화 시 인수"값만" 매개 변수에 전달
∴ 배열 요소값 전체를 전달 X + 포인터 변수 사용하여 주소"값만" 전달 O
➋ 배열 매개 변수 = 포인터 변수
∴ 배열 매개 변수 ➝ 배열 크기와 무관 O

+

High Address ➝ Low Address "할당"

+

함수 호출/실행시 메모리 "할당" ➝ 함수 종료시 메모리 "해제"
Ref)
메인 함수가 가장 아래 위치
사용자정의 함수는 메인 함수 위에 호출된 Code 순서대로 메모리 "할당"(= Stack 쌓임)
사용자정의 함수 실행 종료(Return 반환) ➝ 호출된 Code 역순으로 메모리 "해제"
※ 호출된
만약 호출된 Code 순서가 아니라, 작성된 Code 순서대로 메모리 "할당" 된다면
➝ Compile후(.exe 파일 생성후) Run Time시(.exe 파일 실행시) 메모리 "할당" X
➝ Compile시(.exe 파일 생성시) Hard Disk Storage에 "할당" O
※ Return 반환
"이전으로 되돌아감"의 의미가 사용자정의 함수 실행 종료시 Return 반환하면
그전 위치(= 주소값: 사용자정의 함수가 호출된 위치)로 되돌아간다는 의미에서 용어 지정/사용
+
STACK Overflow
재귀함수(함수 A 내에 A 함수 실행) 사용시, 함수 A 내에 함수 A 실행하는 부분을 잘못 실행
함수 A 내에 함수 A 실행 ➝ 함수 A 내에 함수 A 실행 ➝ 함수 A 내에 함수 A 실행 ➝ ..... 무한 Loop
Stack Sector 메모리 무한 "할당" ➝ HEAP Sector 침범 ➝ STACK Overflow 발생
Ref)
재귀함수 ➝ 메모리 "할당" 多 ➝ 비효율
+
E.g)
CODE (TEXT) Sector의 "Assembly Language Form 1010101 = Parameter 2개를 더하여 Return 해라" 함수 실행의 Local Variable 지역변수, Parameter 매개변수, Return 반환값 등의 메모리 "할당"

#### Operation 동작
메모리 "할당" 고정 영역 X
"할당" / "해제" 영역 O
Ref)
Programme 종료되면, 모든 영역(CODE, DATA, HEAP, STACK) 메모리(RAM)에서 "해제"

STACK Sector
Data를 Control/Management하는 방법중 하나
*   형태: Box 박스
*   방식: LIFO(Last In First Out) 후입선출
*   구조
![](https://t9003081320.p.clickup-attachments.com/t9003081320/56369736-1c02-4b9d-97a8-fb323a7de8f8/Picture1.png)
*   Data + PUSH

Data - POP

*   TOP 가장 "최근"에 STACK에 초기화된 변수/값의 위치

BOTTOM 가장 "처음"에 STACK에 초기화된 변수/값의 위치

E.g.)
*   Codes 순서/위치

(상)

사용자정의 함수 A

사용자정의 함수 B

사용자정의 함수 C (내부에 사용자정의 함수 D)

메인 함수

(하)

*   Run Time시 Codes 실행 순서

메인함수

사용자정의 함수 A 호출

사용자정의 함수 C 호출

사용자정의 함수 B 호출

사용자정의 함수 A 호출

*   STACK "할당" ➝ 해제" 순서

(Bottom)

메인함수 "할당"

사용자정의 함수 A "할당" ➝ 해제"

사용자정의 함수 C "할당" ➝ D "할당" ➝ D "해제" ➝ C "해제"

사용자정의 함수 B "할당" ➝ 해제"

사용자정의 함수 A "할당" ➝ 해제"

메인함수 "해제"

(Top)

HEAP Sector
Data를 Control/Management하는 방법중 하나
*   형태: BINARY TREE 이진트리

Ref) QUEUE

형태: Box 박스

*   방식: "Loose 느슨한"(한번만 비교) 우선순위 QUEUE

| 자료구조 | 삭제되는 요소 |
| ---| --- |
| STACK | 가장 "최근" DATA 후입선출 |
| QUEUE | 가장 "처음" DATA 선입선출 |
| Priority QUEUE | 가장 "우선" DATA ➝ HEAP 으로 구현하는 것이 가장 효율적 |

App)

Simulation System

Network Traffic Control

Task Scheduling in OS

Numerical Analysis

Ref)

Analytic
function을 쪼개서(변형) 분석에 용이하게 해석 (함수 형태의 해로 문제 분석/풀이)
➝ order 순위가 높아질수록(무한대로 갈수록) 本 식과 유사함
Numerical
function이 복잡하더라도 있는그대로 계산 (함수 형태의 해로 문제 접근 복잡 ~~➝ 수치해석~~)

E.g.) Analytic
f: 취업 잘 하고 싶어
일반해
① 일단 학점이 중요해. 연습문제만 많이 풀래.
② 학점도 중요하지만, 실력이 중요해. 깊이 있는 공부를 해야겠어.
③ 양쪽 다 절충이 필요해. ②중심으로 ①을 제대로 수행 해야겠어.
초기값
ⓐ 초기값 = 대학 4년 졸업 후 일단 어디든 바로 취직되는 곳으로 갈래
➝ 특수해 = ①
ⓑ 초기값 = 대학 n년 졸업 후 내가 원하는 곳에서 원하는 일을 하며 살고 싶어
➝ 특수해 = ②
ⓒ 초기값 = 대학 5년 졸업 후 내가 원하는 곳에서 원하는 일을 하며 살고 싶어
➝ 특수해 = ③

*   구조

QUEUE

![](https://t9003081320.p.clickup-attachments.com/t9003081320/427808a2-5e85-420b-81d7-2608cfb651cb/Picture2.png)

우선순위 QUEUE

![](https://t9003081320.p.clickup-attachments.com/t9003081320/147d3a8e-ab7a-443b-b232-f22df95b0046/Picture3.png)

최대값 / 최소값을 찾아내도록 만들어진 자료구조

"Loose 느슨한" 우선순위 QUEUE

➝ 우선순위 QUEUE를 "한번만 비교"하여 실행

Pros) 최대값 / 최소값을 "빠르게" 찾아내도록 만들어진 자료구조

❶ "빠르게" = 큰값이 상위 LEVEL, 작은값이 하위 LEVEL에 있다는 정도 파악

❷ Parent Node 부모노드 > Child Node 자식노드

MAX HEAP 최대힙: Parent Node 부모노드 >= Child Node 자식노드

MIN HEAP 최소힙: Parent Node 부모노드 <= Child Node 자식노드

❸ "한번만 비교" = 중복값(동일값) 허용

**_∴_** Data를 빠르게 ENQUE 쓰고 / DEQUE 읽고 할 수 있음

![](https://t9003081320.p.clickup-attachments.com/t9003081320/67b41631-2dc6-4ede-8fa1-3f8d1636cfab/image.png)
MAX HEAP 최대힙 MIN HEAP 최소힙

"Tight 빡빡한" 우선순위 QUEUE

➝ 우선순위 QUEUE를 "여러번 비교"하여 실행

Cons) Data를 빠르게 ENQUE 쓰고 / DEQUE 읽고 할 때 시간 소모 증가

Pros) Data를 Searching 찾는건 빠름

∵ 정확한 위치를 파악하고 있음

But, ENQUE 쓰고 / DEQUE 읽고 Rearragement 재정렬 시간 소모 증가

*   구현: "Loose 느슨한"(한번만 비교) 우선순위 QUEUE

\- HEAP 구현("할당"/초기화)의 Standard Data Structure 표준 자료구조는 "배열"

\- 구현의 용이성을 위해 배열의 첫번째 위치(Index = 0)은 사용되지 X

\- 특정 위치(Index)의 Node 번호는 새로운 Node가 추가되어도 변하지 않는다

i.e. "배열" index 에 변수 초기화 개념과 동일

\- Parent Node 부모노드 & Child Node 자식노드 관계

. Left Child Node Index = (Parent Node Index) \* 2

. Right Child Node Index = (Parent Node Index) \* 2 + 1

. Parent Node Index = Child Node Index / 2

![](https://t9003081320.p.clickup-attachments.com/t9003081320/0ea81b85-f7b0-4f5d-a7f4-44294e06b089/image.png)

★ HEAP 생성
**heap\_1.c**

```cpp
#define MAX_ELEMENT 200     // HEAP 안에 저장된 요소의 개수

typedef struct
{
  int key;
} element;

typedef struct
{
  element heap[MAX_ELEMENT];
  int heap_size;
} HeapType;

// HEAP 생성
HeapType heap1;


```

★ HEAP 삽입
![](https://t9003081320.p.clickup-attachments.com/t9003081320/064aef4e-462a-4eed-b628-1ad80669f257/maxheap-insertion.png)
**heap\_2.c**

```cpp
#define MAX_ELEMENT 200     // HEAP 안에 저장된 요소의 개수

typedef struct
{
  int key;
} element;

typedef struct
{
  element heap[MAX_ELEMENT];
  int heap_size;
} HeapType;

// HEAP 생성
HeapType heap1;


// 최대힙(MAX HEAP) "삽입" 함수
void insert_max_heap(HeapType *h, element item)
{
  int i;
  i = ++(h->heap_size); // HEAP 크기를 하나 증가

  /* TREE를 거슬러 올라가면서 Parent Node와 비교하는 과정 */
  // i가 ROOT Node(index: 1)이 아니고, 삽입할 Item의 값이 i의 Parent Node(Index: i/2)보다 크면
  while((i != 1) && (item.key > h->heap[i/2].key))
  {
    // i번째 Node와 Parent Node를 교환환다.
    h->heap[i] = h->heap[i/2];
    // 한 LEVEL 위로 올라단다.
    i /= 2;
  }
  h->heap[i] = item; // 새로운 Node 삽입
}


```

★ HEAP 삭제
![](https://t9003081320.p.clickup-attachments.com/t9003081320/b08b3294-fb84-4eb1-b3dd-5ac149a6b5b6/maxheap-delete.png)
**heap\_3.c**

```plain
#define MAX_ELEMENT 200     // HEAP 안에 저장된 요소의 개수

typedef struct
{
  int key;
} element;

typedef struct
{
  element heap[MAX_ELEMENT];
  int heap_size;
} HeapType;

// HEAP 생성
HeapType heap1;


// 최대힙(MAX HEAP) "삽입" 함수:   현재 요소의 개수가 HEAP_Size인 힙 h에 Item을 삽입
void insert_max_heap(HeapType *h, element item)
{
  int i;
  i = ++(h->heap_size); // HEAP 크기를 하나 증가

  /* TREE를 거슬러 올라가면서 Parent Node와 비교하는 과정 */
  // i가 ROOT Node(index: 1)이 아니고, 삽입할 Item의 값이 i의 Parent Node(Index: i/2)보다 크면
  while((i != 1) && (item.key > h->heap[i/2].key))
  {
    // i번째 Node와 Parent Node를 교환환다.
    h->heap[i] = h->heap[i/2];
    // 한 LEVEL 위로 이동
    i /= 2;
  }
  h->heap[i] = item; // 새로운 Node 삽입
}

// 최대힙(MAX HEAP) "삭제" 함수
element delete_max_heap(HeapType *h)
{
  int parent, child;
  element item, temp;

  item = h->heap[1]; // ROOT Node 값을 반환하기 위해 Item에 할당
  temp = h->heap[(h->heap_size)--]; // 마지막 Node를 temp에 할당하고 HEAP 크기를 하나 감소
  parent = 1;
  child = 2;

  while(child <= h->heap_size)
  {
    // 현재 Node의 Child Node 중 더 큰 Child Node 찾기:   ROOT Node의 Left Child Node(index: 2)부터 비교 시작
    if( (child < h->heap_size) && ((h->heap[child].key) < h->heap[child+1].key) )
    {
      child++;
    }
    // 더 큰 Child Node보다 마지막 Node가 크면, while문 중지
    if( temp.key >= h->heap[child].key )
    {
      break;
    }

    // 더 큰 Child Node보다 마지막 Node가 작으면, Parent Node와 더 큰 Child Node를 교환
    h->heap[parent] = h->heap[child];
    // 한 LEVEL 아래로 이동
    parent = child;
    child *= 2;
  }

  // 마지막 Node를 재구성한 위치에 삽입
  h->heap[parent] = temp;
  // 최대값(ROOT Node 값)을 반환
  return item;
}


```

*   힙 정렬 알고리즘 HEAP SORT ALGORITHM

MAX HEAP or MIN HEAP BINARY TREE 구성으로 정렬하는 방식

\- MAX HEAP TREE 구성: 내림차순 정렬

\- MIN HEAP TREE 구성: 오름차순 정렬

과정

E.g.) 내림차순 정렬을 위한 MAX HEAP ALGORITHM 최대힙 알고리즘 구현

ⓐ 정렬해야 할 n개 요소들로 MAX HEAP "BINARY TREE" 내림차순 기준 구성

➝ HEAP은 "1차원 배열"로 쉽게 구현 가능

ⓑ 한번에 요소 1개씩 HEAP에서 추출해 배열의 뒤에서부터 초기화

➝ 정렬해야할 할 n개 요소들을 1차원 배열에 기억한 후

MAX HEAP 삽입을 통해 차례대로 삽입 ★ HEAP 삽입

ⓒ 삭제되는 요소들(최대값부터 삭제)은 값이 감소되는 순서로 정렬

➝ MAX HEAP으로 구성된 배열에서 최대값부터 삭제 ★ HEAP 삭제

**heap\_4.c**

```plain
#define MAX_ELEMENT 200     // HEAP 안에 저장된 요소의 개수

typedef struct
{
  int key;
} element;

typedef struct
{
  element heap[MAX_ELEMENT];
  int heap_size;
} HeapType;

// HEAP 생성
HeapType heap1;


// 최대힙(MAX HEAP) "삽입" 함수:   현재 요소의 개수가 HEAP_Size인 힙 h에 Item을 삽입
void insert_max_heap(HeapType *h, element item)
{
  int i;
  i = ++(h->heap_size); // HEAP 크기를 하나 증가

  /* TREE를 거슬러 올라가면서 Parent Node와 비교하는 과정 */
  // i가 ROOT Node(index: 1)이 아니고, 삽입할 Item의 값이 i의 Parent Node(Index: i/2)보다 크면
  while((i != 1) && (item.key > h->heap[i/2].key))
  {
    // i번째 Node와 Parent Node를 교환환다.
    h->heap[i] = h->heap[i/2];
    // 한 LEVEL 위로 이동
    i /= 2;
  }
  h->heap[i] = item; // 새로운 Node 삽입
}

// 최대힙(MAX HEAP) "삭제" 함수
element delete_max_heap(HeapType *h)
{
  int parent, child;
  element item, temp;

  item = h->heap[1]; // ROOT Node 값을 반환하기 위해 Item에 할당
  temp = h->heap[(h->heap_size)--]; // 마지막 Node를 temp에 할당하고 HEAP 크기를 하나 감소
  parent = 1;
  child = 2;

  while(child <= h->heap_size)
  {
    // 현재 Node의 Child Node 중 더 큰 Child Node 찾기:   ROOT Node의 Left Child Node(index: 2)부터 비교 시작
    if( (child < h->heap_size) && ((h->heap[child].key) < h->heap[child+1].key) )
    {
      child++;
    }
    // 더 큰 Child Node보다 마지막 Node가 크면, while문 중지
    if( temp.key >= h->heap[child].key )
    {
      break;
    }

    // 더 큰 Child Node보다 마지막 Node가 작으면, Parent Node와 더 큰 Child Node를 교환
    h->heap[parent] = h->heap[child];
    // 한 LEVEL 아래로 이동
    parent = child;
    child *= 2;
  }

  // 마지막 Node를 재구성한 위치에 삽입
  h->heap[parent] = temp;
  // 최대값(ROOT Node 값)을 반환
  return item;
}


// Priority QUEUE인 HEAP을 이용한 정렬
void heap_sort(element a[], int n)
{
  int i;
  HeapType h;

  init(&h);

  for(i=0; i<n; i++)
  {
    insert_max_heap(&h, a[i]);
  }

  for(i=(n-1); i>=0; i--)
  {
    a[i] = delete_max_heap(&h);
  }
}


```

Pros) 전체자료 정렬보다는 가장 큰값/작은값 몇개 추출 용이
복잡하지만 효율적인 방법
"시간복잡도"가 좋은편

※ "시간복잡도"
*   HEAP TREE는 완전 BINARY TREE ➝ 전체 높이 ≒ log2n
*   1개 요소 HEAP에 삽입 or 삭제시 HEAP Rearrangement 힙 재정렬 시간 ≒ log2n
*   n개 요소 HEAP에 삽입 or 삭제시 HEAP Rearrangement 힙 재정렬 시간 ≒ nlog2n
E.g.)
Run-Time시 정수 60,000개의 HEAP Rearrangement 힙 재정렬 시간 (Unit: /sec) ≒ 0.034/sec

* * *

## **Example)**

**memory.c**

```cpp
#include <stdio.h>

int func1()
{
    int result = func2();
    return result; 
}

int func2()
{
    return 100;
}

int main(void)
{
    int result;
    result = func1(); 
    printf("%d", result);

    return 0;
}


```

Complie Time
*   2~22번째줄

Codes은 Compile시 .exe 실행 파일 생성후 Hard Disk에 저장

만약 Static 변수가 있으면 Compile 시 할당

Hard Disk 내에 저장된 .exe 실행 파일이 CODE, DATA(Static 변수) 영역에 나누어 저장됨

Run Time
*   실행시작

.exe 실행 파일을 RAM에 복사후 실행

*   15번째줄

함수 `int main` 의 CODE 영역 주소값을 STACK 영역의 가장 아래에 실행 위치 주소값(= Entry Point)으로 할당하여 바로 실행

*   17번째줄

자료형 int의 변수 `result`가 STACK 영역 그 위에 기계어 2진수 형태로 할당

*   18번째줄

① `func1( );`

사용자정의 함수 func1 호출

② `func1`

CODE 영역의 func1 주소값 = 사용자정의 함수 func1 자체가 CODE 영역의 func1 주소값

③ `( )`

CODE 영역에 저장된 func 1 자체의 주소값 아래에 저장된 함수 실행에 대한 Data 내용(기계어

2진수 형태)을 STACK 영역에 func1을 변수(변수 자체 주소값도 존재)처럼 사용하여 할당

※ 만약 인수가 있다면(e.g. func1(10);),

그 위에 인수 자체의 값에 대한 2진수(e.g. 1010) 형태로 할당

*   04번째줄

18번째줄에서

CODE 영역에 저장된 `func1` 자체의 주소값 아래에 저장된 함수 실행에 대한 Data 내용(기계어

2진수 형태)을 STACK 영역에 `func1`을 변수(변수 자체 주소값도 존재)처럼 사용하여 할당할 때

04번째줄 동시 실행

*   05번째줄

중괄호는 Code Block을 나누는 Grammar로 할당 하지 않음

*   06번째줄

자료형 int의 변수 `result`가 STACK 영역 그 위에 기계어 2진수 형태로 할당

*   06번째줄

① `func2( );`

사용자정의 함수 func2 호출

② `func2`

CODE 영역의 func2 주소값 = 사용자정의 함수 func2 자체가 CODE 영역의 func2 주소값

③ `( )`

CODE 영역에 저장된 func2 자체의 주소값 아래에 저장된 함수 실행에 대한 Data 내용(기계어

2진수 형태)을 STACK 영역에 func1을 변수(변수 자체 주소값도 존재)처럼 사용하여 할당

※ 만약 인수가 있다면(e.g. func1(10);),

그 위에 인수 자체의 값에 대한 2진수(e.g. 1010) 형태로 할당

*   10번째줄

06번째줄에서

CODE 영역에 저장된 `func2` 자체의 주소값 아래에 저장된 함수 실행에 대한 Data 내용(기계어

2진수 형태)을 STACK 영역에 `func2` 를 변수(변수 자체 주소값도 존재)처럼 사용하여 할당할 때

10번째줄 동시 실행

*   12번째줄

`return`은

함수 func2 가 실행되고 있는 STACK 영역에 할당된 주소값으로 복귀

\= 값을 전달 ➝ 주소값에 값 초기화

동시에 10~13 번째줄 함수 int func2 관련 부분 할당 해제

*   06번째줄

자료형 int의 변수 `result`에 값을 전달 ➝ 주소값에 값 초기화

*   07번째줄

`return`은

함수 func2 가 실행되고 있는 STACK 영역에 할당된 주소값으로 복귀

\= 값을 전달 ➝ 주소값에 값 초기화

동시에 04~08 번째줄 함수 int func1 관련 부분 할당 해제

*   18번째줄

자료형 int의 변수 `result`에 값을 전달 ➝ 주소값에 값 초기화

*   19번째줄

① `printf("%d", result);`

함수 printf 호출

② `printf`

CODE 영역의 printf 주소값 = 함수 printf 자체가 CODE 영역의 printf 주소값

③ `( )`

CODE 영역에 저장된 printf 자체의 주소값 아래에 저장된 함수 실행에 대한 Data 내용(기계어

2진수 형태)을 STACK 영역에 printf를 변수(변수 자체 주소값도 존재)처럼 사용하여 할당

※ 만약 인수가 있다면(e.g. func1(10);),

그 위에 인수 자체의 값에 대한 2진수(e.g. 1010) 형태로 할당

④ `"%d", result`

"%d" Parameter #1 (char type array, e.g., "<%d> === <%d>")

result Parameter #2 (int type variable, e.g., 변수 result 초기화 값인 인수 100을 전달)

*   19번째줄

`printf` 실행 (Terminal 창에 출력)

동시에 19번째줄 함수 printf 관련 부분 할당 해제

*   20번째줄

`return`은

함수 int main 이 실행되고 있는 STACK 영역에 할당된 주소값(= Entry Point)으로 복귀

\= 값을 전달 ➝ 주소값에 값 초기화

동시에 15~21 번째줄 함수 int main 관련 부분 할당 해제 (17번째줄 변수 result 해제)

* * *

#### **Noticeable Point**

| N-Point #1 | `auto`로 일반 변수 선언시<br> |
| ---| --- |
| N-Point #2 | `static`으로 일반 변수 선언시<br> |
| N-Point #3 | `auto`로 배열 변수 선언시<br> |
| N-Point #4<br> | `static`으로 배열 변수 선언시 |