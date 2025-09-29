# Complie & Run Time (Concept)

# **Compile Time**
> 정적인 (Memory RAM 용량의 크기가 정해져야 가능한) 작업들 진행

## 1. 전체 소스 코드 분석

개발자가 작성한 소스 코드 분석 (위 ➝ 아래)

**구문 분석 (Syntax Analysis)**


개발자가 작성한 소스 코드 ➝ Programming Language Grammar Check


<details><summary> Grammar Check </summary>



```cpp
#include <stdio.h>

int main() 
{
    int x = 10     // ; 부재  ➝  Compile Error 발생 
    return 0;
}


```

구문 오류 → Compile Error
>  실행파일 자체가 만들어지 않음

`Run Time Error ≠ Compile Error`

EX ) Run Time Error 

- Code가 실행중 발생하는 오류
- Code가 잘못된 Memory (RAM)에 접근하려고 할때 발생
    -  포인터(주소값)가 할당하지 않은 Memory를 참조할 때
    - 포인터(주소값)가 가르키는/참조하는 값이 존재하지 않을 때
        -  배열의 범위를 벗어난 위치에 접근할 때

>  Programme의 비정상 종료를 야기





</details><br>





<details><summary> 1. Tokenisation 토큰화 </summary>

```cpp
int main() 
{
    int x = 10;     // 정수 자료형 변수 X를 선언 + 정수 10을 형변환 없이 "동시" 초기화
    int y = x + 5;

    return 0;
} 
   
```

**Tokenisation 토큰화**
Codes를 개별 Token으로 Codes 작성 순서(∵ Compile Time 일부: 위 ➝ 아래)에 맞춰 분해/해체


> Codes의 기본 구성 요소 Unit
 

| **code** | **토큰화** |
| ---| --- |
| `int` |  (키워드) |
|  `main` | (함수 이름)  |
|  `()` | (괄호, 함수 인자를 나타냄)   |
|  `{` | (중괄호 시작)  |
|  `int` | (키워드)  |
|  `x` | (변수 이름)  |
|  `=` | (할당 연산자)   |
|  `10` | (상수)   |
|  `;` | (문장 종료 기호)  |
|  `int`| (키워드)   |
|  `y` | (변수 이름)   |
|  `=` | (할당 연산자)  |
|  `x` | (변수 이름)   |
|  `+` | (덧셈 연산자)  |
|  `5` | (상수)  |
|  `;` | (문장 종료 기호)   |
|  `return`| (키워드)   |
|  `0` | (상수)  |
|  `;` | (문장 종료 기호)   |
|  `}` | (중괄호 끝)   |



</details><br>


<details><summary> 2. Syntax Tree 구문트리 생성 </summary>



Tokenisation Unit를 기반으로 Syntax Tree 생성 ➝ Programme(Codes) 구조를 계층화

```cpp
                   main()
                     |
                   {...}
                     |
    ------------------------------------
   |                 |                  |
  int x=10     int y = x + 5         return 0
                     |
                     +
                  |     |
                  x     5
   
```

- 구문트리 최상위 계층에 메인 함수 `main( )` 위치
- 아래에 메인 함수 `main( )` 내부를 구성하는 Code Block의 시작과 끝을 의미하는 `{ }` 위치
- 메인 함수 `main( )` 내부의 구성 요소 파악
- 첫번째 변수 선언(할당), "동시" 초기화 ➝ `int x = 10`
- 두번째 변수 선언(할당), "동시" 첫번째 변수를 사용한 연산값을 초기화 ➝ `int y = x + 5`
- 반환문 ➝ `return 0`

※ `int y = x + 5`
`int` 정수 자료형 변수 `y` 를 선언(할당)
"동시" `int` 정수 자료형 변수 `x` 와 정수 `5` 를 `+` 더한값 초기화
<br>
※ `main ()` ➝ Root Node 근원 노드
`+` ➝ Parent Node 부모 노드
`x`와 `5` ➝ Child Node 자식 노드
<br>
※ "Step #2) Syntax Tree 구문트리 생성"을 통해 Compiler는 Code Structure & Link 이해
  - 문법 검사 수행
  - 컴파일러 최적화 수행의 기반 활동

### 의미 분석 (Semantic Analysis)

Semantic Analysis Syntax Analysis에서 생성된 Syntax Tree가 의미적 규칙을 준수하는지 확인

① 변수 타입 검사, 변수와 함수의 선언과 사용의 일관성, 올바른 표현식 여부 검사 실행

② Scope Rules 스코프(범위) 규칙 실행

\= 변수, 함수의 유효 범위 정의

➝ Life Cycle 생존 기간

➝ Where/When 어디에서/언제 사용하는지

</details><br>



⇒ Grammar Check 문법 검사 수행 (문법 검사 否 통과시 Compile 중단, e.g. Compile Error)




<details><summary> EX) Grammar Check 문법 검사 </summary>
**3.c**

```cpp
#include <stdio.h>

int main() 
{
    int x = "Hello, World!"; // int 정수 자료형 변수 a 선언 "동시" 문자열 초기화
                             // ➝  Compile Error 발생 (헤결: int x = 10;)    

    return 0;
}     


```

타입 오류 ➝ Compile Error O

**Example) Semantic Analysis**
E.g.) 변수
1) Global Scope (전역 스코프) ➝ 예: Global Variable 전역 변수
\- Programme 전체에서 사용 가능 O
\- Programme 전체에서 접근 가능 O
2) Local Scope (지역 스코프) ➝ 예: Local Variable 지역 변수
\- 해당 범위내에서만 사용 가능 O ➝ 예: Local Variable 지역 변수 위치한 `{ }` 내에서만
\- 해당 범위내에서만 접근 가능 O ➝ 예: Local Variable 지역 변수 위치한 `{ }` 내에서만
**sr\_v.c**

```cpp
#include <stdio.h>

int x = 20; // 전역 변수 ➝ 아파트 집 주인

int main()
{
    printf("%d\n", x); // 전역 변수 출력: 20 ➝  아파트 집 주인

    int x = 10;        // 지역 변수 1 (메인 함수 Code Block {  } 내에서만 유효) ➝ 전제인
    printf("%d\n", x); // 지역 변수 1 출력: 10
    {
        int x = 5;         // 더 제한된 지역 변수 2 (현재 Code Block {  } 내에서만 유효) ➝ 전세인이 임대한 또 다른 내부적 전세인
        printf("%d\n", x); // 지역 변수 2 출력: 5
    }
    printf("%d\n", x); // 지역 변수 1 출력: 10

    return 0;
}
// 프로그램 종료시 땅부지만 남고 아파트는 허물어짐 (집 존재 X)              
```

Scope Rules이 적용되어 동일 이름의 변수를 다른 Scope에 사용 가능 O

E.g.) 함수
**sr\_f.c**

```cpp
#include <stdio.h>

// 사용자정의 함수 
int add(int a, int b)
{
   return a + b;
}

// 메인 함수
int main()
{
   int num1, num2, sum;

   printf("첫 번째 숫자를 입력하세요: ");
   scanf("%d", &num1);

   printf("두 번째 숫자를 입력하세요: ");
   scanf("%d", &num2);

   sum = add(num1, num2);

   printf("합계: %d\n", sum);

   return 0;
}   
           
```

05번째줄 사용자정의 함수 실행의 Life Cycle은 08번째줄 실행후 종료
➝ 07번째줄 Return 반환후 종료
Return 반환 아래 Codes가 있더라도 실행 X
∵ 함수의 Return 반환 = 함수의 종료
</details><br>



## 2. 컴파일러 최적화 


Memory 사용 최소화 + Programmme 실행 속도 향상 위해, 소스 코드 개선

※ 아파트 단지 다수 인구 이사 보다 소수 인구 이사가 이사 속도 빠름

① Codes Modification 코드 수정
② Codes Reconstruction 코드 재구성
E.g)
불필요한 계산 제거, 공통 표현식 제거, 반복의 최소화 등을 위한 재구성

**Example) Optimisation**
**opt.c**

```cpp
#include <stdio.h>

int calculate() 
{
    int result = 0;
    for (int i = 0; i < 100; i++) 
    {
        result += i;
    }
    return result;
}

int main() 
{
    int sum = calculate();
    return 0;
} 
           
```

↓ (내부적) 최적화

```cpp
#include <stdio.h>

int main() 
{
    int sum = 4950;  // 上 Code 4번째 ~ 12번째줄 결과: 11번째줄 return 값 = restult = 4950 = 고정 결과값
    return 0;
}
           
```

`calculate( ) = 4950`

## 3. 기계어 코드 생성

개발자가 작성한 소스코드를 컴퓨터가 이해하는 기계어로 변환후 실행 가능한 파일 생성

CPU에서 실행 가능한 파일(.exe) 생성
Hard Disk Storage 할당

* * *

# **Run Time**

>  동적인 (Memory RAM 용량의 크기가 Compile Time에 정해지지 않아도 가능한) 작업 진행
> -  자료형, 지역 변수/매개 변수 등등

실행 가능한 파일을 실행 = 실제 Programme(Code) 실행 흐름이 이루어짐<br>
① Hard Disk에 할당된 실행 가능한 파일 (.exe)을 Memory (RAM)에 복사 할당<br>
② OS 운영체제는 실행가능한 파일에서 Programme(Code) 진입점(= 메인 함수 주소값) 탐색<br>
③ CPU에서 Memory (RAM)에 접근하여 실행 가능한 파일 (.exe) 실행