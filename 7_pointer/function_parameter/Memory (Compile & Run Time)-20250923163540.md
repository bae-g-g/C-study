# Memory (Compile & Run Time)

## **Compile Time**

![](https://t9003081320.p.clickup-attachments.com/t9003081320/b9f54e27-43ad-4f12-b59f-e8dcd037c858/image.png)

#### **Phase #1) Preprocessing 전처리**
*   #으로 시작되는 Code Texts 처리 (e.g., #include < >, #define )
*   .c 확장자명의 File ➝ .i 확장자명의 File

개발자가 작성한 소스코드 파일 ➝ 전처리된 소스코드 파일

★ 下 Step #1-A) 1-B) 1-C)는 "동시"에 처리

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
개발자
소스코드
↓
어셈블리어
↓
기계어
Computer

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

Cf)
Static 변수의 문법검사 후 Memory 할당 수행 (More details in the section below ☆)

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

* * *

## **Understanding**

**compile\_run\_1.c**

```cpp
// Static #1-1:  General Data Type
#include <stdio.h>

void function (int Y)   
{
   
}

int main ()
{
   int X;          
   function(X);   

   return 0;
}

// Static #1-2:  Array Data Type
#include <stdio.h>

void function (int Y[])   
{
   
}

int main ()
{
   int X[];          
   function(X);   

   return 0;
}

///////////////////////////////////

// Static #2-1:  General Data Type
#include <stdio.h>

void function (static int Y)  
{

}

int main ()
{
   static int X;
   function(X);

   return 0;
}

// Static #2-2:  Array Data Type
#include <stdio.h>

void function (static int Y[3])    
{

}

int main ()
{
   static int X[3];
   function(X);

   return 0;
}


```

#### **Understanding #1)** Static 지역 변수 가능 O + Static 매개 변수 가능 X
➝ Static 변수의 문법검사 후 Memory 할당 수행 (More details in the section below ☆)

매개 변수 = register 변수
➝ static 변수 선언 불가 (매개 변수 static 변수로 선언시 문법 검사 오류 발생 → Compile Error)
∵
1) auto 매개 변수 처리 방식
RAM에 인수 할당 ➝ CPU Register에 초기화 ➝ CPU Register에서 처리 ➝ 처리한 값 RAM에 전달
2) static 매개 변수 처리 방식
CPU Register에 초기화 ➝ CPU Register에서 처리
∴
매개 변수 = register 변수

Ref)
Variable Storage Class 4 Types
*   auto

Memory (RAM) - STACK 영역 할당

*   register

CPU 할당

*   static

Memory (RAM) - DATA 영역 할당

*   extern

Memory (RAM) - DATA 영역 할당 (외부 Files의 변수)

※ \[CH08A\] Variable (Lecture) 참조
※ \[CH09A\] Pointer (Lecture) > Function > Memory (Management + Structure + Operation) 참조

**compile\_run\_2.c**

```cpp
#include <stdio.h>

// 젼역 변수 (문법 = static 고정)
int a;               // =  static int a
static int b;        // =  int b
auto int c;          // Complie Error: Complie 과정중 2번째 단계에서 문법 검사 오류 (static int를 auto int로 변경 불가하게 막아 놓음)
register int d;      // Complie Error: Complie 과정중 2번째 단계에서 문법 검사 오류 (static int를 register int로 변경 불가하게 막아 놓음)

// 매개변수 (문법 = register 고정)
int function1(int e)        // =  register int a
{
   return 0;
}

int function2(register int f)
{
   return 0;
}

int function3(static int f) // Complie Error
{
   return 0;
}

int function4(auto int f)  // Complie Error
{
   return 0;
}

// 지역변수 (문법 = Default Storage Class는 auto 지만 Complie 과정중 2번째 단계에서 다른 Storage Class를 사용하더라도 문법 검사에서 막아 놓지 않음)
int main ()
{
   
   int g;
   auto int h;
   static int i;
   register int j;

   return 0;
}


```

#### **Understanding #2) 배열 크기 有 ➝ 지역 변수 가능 O**
#### **Understanding #3) 배열 크기 有 ➝ 매개 변수 가능 O**

① 지역 변수 가능 O

② 매개 변수 가능 O (매개 변수 = register 변수: CPU Register에 초기화 ➝ CPU Register에서 처리)
∵
배열 ➝(붕괴)➝ 포인터 (컴파일 2단계)

②-ⓐ int X\[3\] or int X\[10\] 경우 포인터로 붕괴 처리하여 어떤 배열 Index 에서도 주소값으로 접근 O
➝ 어셈블리어 (下 Image 오른쪽) Red Coloured Texts (QWORD PTR, DWORD PTR) 참조
![](https://t9003081320.p.clickup-attachments.com/t9003081320/de66b2a1-301b-44a3-ad05-64f32477dfcf/image%20(2).png)

②-ⓑ 붕괴처리 예외 2 Cases (sizeof, &)는 소스 코드(下 Image 왼쪽)에서 배열로 처리 후
컴파일 2단계에서 "배열로 처리하는 형식"으로 붕괴 처리
➝ 어셈블리어 (下 Image 오른쪽) 19번째줄, 25번째줄 포인터 연산 단위 20, 40 참조
![](https://t9003081320.p.clickup-attachments.com/t9003081320/90d935e5-90c5-4d52-9c6c-9734162195c1/image%20(3).png)

**compile\_run\_3.c**
*   매개변수 = register 변수
*   배열 ➝(붕괴)➝ 포인터 변수

```cpp
#include <stdio.h>

void function_1(register int Y[5])  // 매개변수 = register 변수
{
   printf("%d\n", sizeof(Y));       // 배열 ➝(붕괴)➝ 포인터 변수
}

int function_2(int Z[5])            // 매개변수 = register 변수 (defualt)
{
   return sizeof(Z);                // 배열 ➝(붕괴)➝ 포인터 변수
}

int main ()
{
   int X[0];

   function_1(0);
   printf("%d\n", function_2(0));

   return 0;
}


```

#### **Understanding #4) 배열 크기 無 ➝ 지역 변수 가능 X**
지역 변수는 Run Time 시 할당(Memroy RAM - STACK)되는데도 불구하고, Complie Error 발생
∵
Run Time 시 할당되지만, Complie 과정에서 문법 검사 통과 X
➝ Run Time시 Memory 할당 크기를 정확하게 하기위해서, 사전 Compile시 배열 크기 파악 필요 O
➝ 배열 크기 = 0 (e.g., int X\[0\];) 일지라도, 배열 크기 파악되기 때문에, Compile Error 발생 X
∴
배열은 지역 변수 사용시 배열 크기 없이 사용 불가 O
**compile\_run\_4.c**

```cpp
#include <stdio.h>

int main ()
{
   int X[0];   // 배열 크기 有 + 지역 변수 가능 O 
   // int Y[];    // 배열 크기 無 + 지역 변수 가능 X
   return 0;
}


```

Ref)
int X, float Y, char Z는 배열과 달리 Compile Error가 발생 X
∵
Compile 시 각각 4 Bytes, 4 Bytes, 1 Byte의 정확한 Memory 할당 크기 파악 가능 O
If)
int X, int array\[\], float Y, char Z 선언 시, 배열 array 크기가 명확하지 않음
➝ float Y의 Memory 할당 위치 (주소값)를 정확하게 Compile 시 파악 가능 X (i.e. Run Time에 영향)
➝ Run Time에 영향
∴ Run Time에 영향 없도록, 사전 Compile Error 발생 하도록 Set-Up

#### **Understanding #5) 배열 크기 無 ➝ 매개 변수 가능 O**
① 문법 정의: 인수 ➝(초기화)➝ 매개 변수: 초기화 시 인수"값만" 매개 변수에 전달
➝ 배열 적용
∴
문법 정의: 배열 요소값 전체를 전달 X + 포인터 변수 사용하여 주소"값만" 전달 O
+
② 배열 전체 요소값 한번에/동시에 재초기화 가능 X
E.g.)
int X\[3\] = {1, 2 ,3};
X = {4, 5, 6}; // Compile Error 발생 O

일반 변수값 한번에/동시에 재초기화 가능 O
Ref)
int X = 3;
X = 9; // Compile Error 발생 X

↓
③ 문법 정의: 배열 매개 변수 ➝(붕괴)➝ 포인터 변수 (주소값)

∴ 배열 매개 변수 = 포인터 변수 (= 주소값, ≠ 배열 전체 요소값)으로 처리
∴ 배열 매개 변수 ➝ 배열 크기와 무관 O

**compile\_run\_5.c**
*   배열 크기 無 ➝ 지역 변수 가능 O + 매개 변수 가능 O

배열 크기 無 ➝ 지역 변수 가능 X + 매개 변수 가능 O

*   배열 ➝(붕괴)➝ 포인터 변수

```perl

#include <stdio.h>

void function(int X[])
{  
   // 배열 크기 無 ➝  매개 변수 가능 O 
   // 배열 ➝(붕괴)➝ 포인터 변수
   printf("%d\n", X);
   printf("%d\n", X + 1);
   printf("%d\n", X + 2);
   printf("%d\n\n", *X);

   // 배열 크기 有 ➝ 지역 변수 가능 O 
   int Y[5] = {4, 5, 6, 7, 8};
   printf("%d\n", &Y);
   printf("%d\n", &Y + 1);
   printf("%d\n", &Y + 2);
   printf("%d\n", *&Y);
   printf("%d\n", **&Y);

   // 배열 크기 無 ➝ 지역 변수 가능 X
   // int Z[];
}

int main()
{
   int X[3] = {1, 2, 3};
   function(X);
   return 0;
}


```