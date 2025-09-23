# Function #2 (Function Pointer Variable)

# **Function Pointer Variable 함수 포인터 변수**

## **Concept 개념**
함수 포인터 변수 = 함수의 주소값(Code Sector에 위치) 초기화 포인터 변수

#### Concept #1
*   함수(자체) ≒ 함수의 주소값
*   함수(자체) ≠ 함수의 주소값
Ref)
int a = 10; // a = 10 (a 주소값 下에 10이 초기화 되어있는 의미 O ➝ a와 10이 동일함을 의미 X)

#### Concept #2
*   int 변수의 주소값 초기화 포인터 변수 = int 포인터 변수
*   char 변수의 주소값 초기화 포인터 변수 = char 포인터 변수
*   함수의 주소값 초기화 포인터 변수 = 함수 포인터 변수
Ref)
자료형 포인터 변수 주요 용도
\= 주소값 통해 변수에 접근 후 사용 (변수 값 호출/변경)
함수 포인터 변수 주요 용도
\= 주소값 통해 함수에 접근 후 사용 (함수 호출/~~변경~~)
※ ~~변경~~
ⓐ 함수 저장 Code Sector는 (Stack Sector에 저장되는 변수와 달리) Compile 이후 변경 不가능
➝ 변수 const와 유사
ⓑ 함수 포인터 변수를 통해 함수 호출 가능
➝ 함수(자체) 변경 不가능 (e.g. add 함수 자체를 remove 함수로 변경 不가눙)

## **Usage 용도**
① 함수 포인터 변수로
함수 호출/실행

② 함수 포인터 변수는
함수 포인터 변수에 초기화된 주소값에 해당하는 다른 함수를 실행

③ Call Back Function 콜백 함수
메인 함수 내 함수 foo 호출의 인자인 함수 포인터 변수를
함수 foo의 매개 변수로 전달할 때,
그 매개 변수에 해당하는 함수 포인터 변수에 해당하는 함수
\= 콜백 함수

※ 콜백 함수
≒ 콜백 함수 주소값
\= 메인 함수 내 함수 foo 호출의 인자
\= 함수 foo의 매개 변수

**func\_cb\_1.c**

```plain
콜백 함수(  )
{

}

function foo (매개변수 = 콜백 함수 주소값)
{
   콜백 함수 실행 코드 // 콜백 함수의 주소값을 사용하는 코드 포함
}


메인 함수
{

  foo (인자 = 콜백 함수 주소값);

}


```

🅐 02번째줄 콜백 함수에 해당하는 함수가 있고
🅑 16번째줄 함수 foo의 인자로 02번째줄 콜백 함수의 주소값을 전달 받아
🅒 07번째줄 함수 foo를 (02번째줄 콜백함수의 주소값을 매개변수로)실행하면서
🅓 09번째줄 함수 foo의 콜백 함수 실행 코드 (02번째줄 콜백함수의 주소값을 사
용 하는 코드 내용 포함)를 실행

**Call Back Function Feature 콜백 함수 특징**
ⓐ 콜백 함수 자료형 = 인자 자료형 = 매개변수 자료형
ⓑ Call Back 함수 ➝(직관적 이해)➝ Call After 함수
ⓒ C언어(순차적 작동) 콜백 함수(동시 작동) 사용 빈번도 下

**Call Back Function Usability 콜백 함수 유용성**
ⓐ Flexibility 유연성
ⓑ Modularity 모듈성 (Blockfication 블럭화)
ⓒ Reusability 재사용성

④ 함수 실행 중 다른 함수 생성 (함수 포인터 변수를 함수 리턴값으로 사용)

## **Declaration & Initialisation 선언 및 초기화**

#### Procedure 절차
① 함수 선언
e.g., `void func( );`
② 함수 포인터 변수 선언
e.g., `void (*func_ptr)( );`
③ 함수 주소값 초기화
e.g., `func_ptr = func` ∵ 함수(자체) ≒ 함수의 주소값
④ 함수 포인터 변수를 통해 함수 호출(=실행)
e.g., `func_ptr( );`

#### Data Type & The Number of Parameter 자료형 및 매개변수 갯수
*   함수(자체) 자료형 = 함수 포인터 변수 자료형
ⓐ Return 값 자료형
ⓑ 매개 변수 자료형
*   함수(자체) 매개 변수 갯수 = 함수 포인터 변수 매개 변수 갯수
E.g)
*   함수 자료형 및 매개 변수 갯수 #1

: void func( );

함수 포인터 변수 자료형 및 매개 변수 갯수 #1

: void (\*func\_ptr)( );

*   함수 자료형 및 매개 변수 갯수 #2

: int func( );

함수 포인터 변수 자료형 및 매개 변수 갯수 #2

: int (\*func\_ptr)( );

*   함수 자료형 및 매개 변수 갯수 #3

: int func(int x, int y);

함수 포인터 변수 자료형 및 매개 변수 갯수 #3

: int (\*func\_ptr)(int, int);

#### 함수(자체) ≒ 함수의 주소값
함수 주소값 출력
함수 名(자체)으로 값 출력
기계어로 저장된 Code Sector의 함수 주소값 출력
∴ 함수(자체) ≒ 함수의 주소값
**func\_cb\_2.c**

```cpp
#include <stdio.h>

void version_info()
{
    printf("version 1 app\n");
    return;
}

int main()
{
    printf("function의 주소: %d\n", version_info);
    printf("function의 size: %d\n", sizeof(version_info));  

// 왜 Size가 1 Byte인가? 주소값 = 함수 포인터 변수 크기 8 Bytes 아닌가? 
// 함수 자체  ≒  함수의 주소값
// 함수자체는 L-Value (e.g., 변수 A), 함수 주소값은 R-Value (e.g., 가리키는 값 10) 

//  Code(Text) Sector에 기계어 형태로 초기화된 함수의 주소값 출력 
//  = 함수도 변수처럼 할당 공간을 가지고 있음
//    Code Sector ➝(X)➝ Stack Sector: 함수 호출/실행을 하지 았았으므로 Stack Sector에 할당 X
}


```

####   

#### Function & Address
함수 포인터 변수의 Size는 OS 운영체제에 따라 상이
운영체제 마다 포인터 변수 크기가 다른 것과 동일 맥락
[![](https://t9003081320.p.clickup-attachments.com/t9003081320/5bfdae41-b87d-40d7-9eef-52e7597c5dcd/image.png)](https://cboard.cprogramming.com/c-programming/108747-size-function-pointer.html)

#### L-Value vs R-Value
*   L-Value(_l-value_)

(참조하는/가리키는 값)참조하는/가리키는 주체 = 변수 자체

*   R-Value(_r-value_)

(임시 초기화 값)참조하는/가리키는 값 = 변수 초기화 값

E.g)
int A = 10;
A = A + 10; //  오른쪽에 있으므로 변수 A가 아니라 변수값 10을 의미
Ref)
*   왼쪽 = 변수
*   오른쪽 = 초기화 값 (변수名 형식을 취하더라도 초기화 값, e.g., A)
∴
*   함수(자체) = 함수名 변수 = L-Value(_l-value_)
*   함수(자체) 출력값 = 함수名 변수 주소값 = R-Value(_r-value_)
※
L-Value(_l-value_) Conversion 형변환이 일어나는 경우

* * *

Usage #1 ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-6498](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-6498))

Usage #2 ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-6578](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-6578))

Usage #3 ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-6538](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-6538))

Usage #4 ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-6558](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-6558))