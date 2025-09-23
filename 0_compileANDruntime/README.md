# + Complie & Run Time (C)

# **C/C++**

|  | **Compile** | **Run** |
| ---| ---| --- |
| 작 동 | 소스 코드 ➝ 기계어 | 기계어 |
| 가상 머신 | 가상 머신 無 |
| 중간 코드 | 중간 코드 無: 소스 코드 ➝(Direct)➝ 기계어 |
| 파 일 | .c / .cpp ➝ .exe | .exe |
| 할 당 | Hard Disk | Hard Disk ➝ RAM |
| 엔 진 | CPU에 의해 Compiler가 | OS에 의해 RAM에 접근하여 CPU가 |
| 유 형 | 컴파일 언어 |

## **Compile**

CPU에서 실행 가능한 파일(.exe) 생성(Compile)
① 컴파일러가 개발자가 작성한 소스 코드(.c / .cpp) 파일 Open
② Open한 소스 코드를 위 ➝ 아래로 해석
Ref) Syntax Analysis (Tockenisation + Syntax Tree) 수행
③ 개발자가 작성한 소스 코드(.c / .cpp) ➝ 컴퓨터가 해석할 수 있는 기계어(.exe)
Ref) Semantic Analysis (Scope Rules) 수행
개발자 소스 코드 (컴퓨터는 해석 X): Hard Disk
↓ Compile
컴퓨터 기계어 (컴퓨터는 해석 O): CPU
④ CPU에서 실행 가능한 파일 (.exe) 생성 (특정 OS 운영체제에 맞는 기계어 형태로 구성)
∴ Window OS와 Mac OS와 실행 결과 상이
⑤ Hard Disk에 할당

## **Run**

CPU에서 실행 가능한 파일(.exe) 실행(Run)
① OS에 의해 Hard Disk에 할당된 실행 가능한 파일(.exe)을 Memory(RAM)에 복사 할당(Loading)
② OS에 의해 실행가능한 파일(.exe)에서 Programme(Code) 진입점(RAM에서 주소값) 탐색
③ OS에 의해 진입점(RAM에서 주소값)을 CPU에 전달
④ CPU에 의해 진입점(RAM에서 주소값)에 접근하여 주소값 下에 저장된 기계어 실행
CPU
Memory에서 (주소값 下에 저장된 기계어) 명령어를 읽어 실행하는 Hardware
ROM
Computer Booting System Information, Bios/Firmware Software, Initialisation, etc.,에
필요한 변경 불가능/어려운 기본 Codes를 할당하는데 사용

* * *

## **Compile +**

![](https://t9003081320.p.clickup-attachments.com/t9003081320/b9f54e27-43ad-4f12-b59f-e8dcd037c858/image.png)

#### **Phase #1) Preprocessing 전처리**
*   #으로 시작되는 Code Texts 처리 (e.g., #include < >, #define )
*   .c 확장자명의 File ➝ .i 확장자명의 File

개발자가 작성한 소스코드 파일 ➝ 전처리된 소스코드 파일

★ 下 Step #1-A) 1-B) 1-C)는 "동시"에 "병행" 처리

Step #1-A) Header File 헤더 파일 처리
#include < >내 해당 내부 Codes를 복사하여 개발자가 작성한 소스코드 위치에 Code Texts "만" 삽입

```cpp
#include <stdio.h>  // stdio.h  Header File의 printf 함수 내부 Codes를 복사하여 여기 위치에 그대로 삽입

int main()
{
  printf("Hello");  
}


```

Step #1-B) Macro 매크로 처리
#define 처리

```cpp
#define PI 3.14   // PI = 3.14로 정의

int main()
{
    float X = PI; // 1단계 전처리후 float X = 3.14
}


```

Step #1-C) 주석제거
개발자가 작성한 소스코드의 주석 제거

#### **Phase #2) Compile 컴파일**
*   개발자가 작성한 소스코드와 Computer가 처리하는 기계어 사이의 어셈블리어로 처리

어셈블리어

\- 개발자가 이해 가능 O

\- 명백한 기계어 X

\- 명백한 기계어와 1대1 대응/치환 되는 언어

\- Computer가 이해 가능 X

![](https://t9003081320.p.clickup-attachments.com/t9003081320/54f4327c-ee2d-4640-bb65-035ad84e038f/image%20(1).png)

※
개발자 소스코드
↓
어셈블리어
↓
컴퓨터 기계어

※
Computer의 구조에 따라 기계어가 다름 (∴ Window OS, Mac OS 처리 간극 발생)
CPU에 따라 지원하는 Operation 유형과 갯수 다름

*   .i 확장자명의 File ➝ .s 확장자명의 File

전처리된 소스코드 파일 ➝ 어셈블리어 파일 (기계어 X)

*   Grammar Check 진행
구문분석

① 토큰화 (Tokenization)

② 구문트리 (Syntax Tree) 생성

의미분석

\- 스코프 규칙 (Scope Rules): 전역 스코프(Global Scope) + 지역 스코프(Local Scope)

#### **Phase #3) Assemble 어셈블**
*   .i 확장자명의 File ➝ .s 확장자명의 File

어셈블리어로 된 어셈블리어 파일 ➝ 기계어로된 오브젝트 파일

기계어

\- 개발자가 이해 가능 X

\- 명백한 기계어 O (Bianary 2진수 Files 생성, e.g., 10011101 ..... 로 작성된 Codes)

\- Computer가 이해 가능 O

#### **Phase #4) Link 링크**
*   Linker 링커를 통해 오브젝트 파일을 "연결/묶음" 하여 실행 파일(.exe)파일로 생성
E.g.)
main.c, user\_1.c, user\_2.c
↓ (소스코드 파일 ➝ 어셈블리어 파일➝ 기계어 오브젝트 파일 변경)
main.o, user\_1.o, user\_2.o
↓ (연결/묶음 ➝ 실행 파일 생성)
.exe

### **Example)**
Programme = (**main.h** \+ **main.c**) + (**user\_1.h** + **user\_1.c**) + (**user\_2.h** + **user\_2.c**)

**main.h**

```cpp
// 메크로 설정
#define PI 3.14      

int X = 10;          // 여기 라이브러리 내에서도 전역변수, 전처리과정에서 이 라이브러리 작성 코드 위치에 삽입되어 전역변수

int var_Y ()
{
    int Y = 20;      // 여기 라이브러리 내에서는 지역변수, 전처리과정에서 이 라이브러리 작성 코드 위치에 삽입되어 지역변수

    return Y;
}


```

**main.c**

```cpp
#include <stdio.h>   // 이미 user_1.h, user_2.h에서 include 되었기 때문에 없어도 됨
#include "main.h"    // 사용자정의 라이브러리 문법:  #include " "
#include "user_1.h"   
#include "user_2.h"

int main()
{
   function_1();        // user_1.c의 함수
  function_2();        // user_1.c의 함수
  printf("%d  %d\n",  X, var_Y());
}


```

+
**user\_1.h**

```cpp
// stdio.h를 사용한 개발자 정의 라이브러리:  함수 1 선언
#include <stdio.h>

void function_1();  // 함수 1 선언


```

**user\_1.c**

```cpp
#include <stdio.h>
#include "user_1.h"

void function_1()
{
  printf("Programming #1\n");   // user_1 라이브러리내 함수 1 초기화
}


```

+
**user\_2.h**

```cpp
// stdio.h를 사용한 개발자 정의 라이브러리:  함수 2 선언
#include <stdio.h>

void function_2();  // 함수 2 선언


```

**user\_2.c**

```cpp
#include <stdio.h>
#include "user_2.h"

void function_2()
{
  printf("Programming #2\n");  // user_2 라이브러리내 함수 2 초기화
}


```

#### **실행**
① Terminal Window 터미널 창에서 Folder Path Exploration 폴더 경로 탐색
cd ./ tab

② gcc \-o 생성할 파일명 file1.c file2.c file3.c .... 을 입력 (파일 및 옵션은 띄어쓰기 구분)
E.g.)
`gcc -o execution_file .\main.c .\user_1.c .\user_2.c`
➝ main.c user1.c . user2.c의 파일들을 컴파일 3단계에서 오브젝트파일로 만들고 연결/묶음
➝ 실행 파일 (.exe) 생성

③ ./ 실행 파일명
E.g.)
`./ execution_file`