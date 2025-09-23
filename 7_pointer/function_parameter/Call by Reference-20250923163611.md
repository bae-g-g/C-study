# Call by Reference

## **Call by Reference**
#### 사용자정의 함수의 매개변수 = 레퍼런스 변수
메인 함수의 Local Variable 통채를("변수값 + 주소값") 사용자정의 함수의 Parameter에 초기화(복사)
≒ Call by Value + Call by Address
메인 함수의 지역 변수 Local Variable = 사용자정의 함수의 매개변수 Parameter
\= 메인 함수의 지역 변수 Local Variable와 사용자정의 함수의 매개변수 Parameter가 "완전히" 동일
\= 메인 함수의 지역 변수 Local Variable와 사용자정의 함수의 매개변수 Parameter가 실제 "동기화"
∴
메인 함수 변수의 변수값 = 사용자정의 함수의 매개변수의 변수값
메인 함수 변수의 주소값 = 사용자정의 함수의 매개변수의 주소값
Ref)
메인 함수 Local Variable 지역 변수 변수값은 사용자정의 함수에 따라 "보존 or 변경" 가능 O
∵ Call by Address 특징 내재
사용자정의 함수 실행 ➝ 메인 함수의 지역 변수 A, B의 주소값에 접근해서 A, B 값변경 O
Cf)
Call by Reference와 Call by Address의 변경 방법은 상이
∵ Call by Address는 주소값에 접근하여 변수값 변경
∵ Call by Reference는 변수값 자체를 변경 (결국 별명이 다른 다같은 동일 변수이기 때문)

*   Pros

초기화(복사)하지 않고 직접 참조

변수 자체를 변경

\= 별명이 n개인 다같은 "동일" 변수

\= 별명이 n개인 "1개" 변수

\= 불리는 이름이 다를뿐 본인은 1명으로 변하지 않음

Code 실행 속도 증가

*   Cons

직접 참조하기 때문에 本 변수값이 변경이 되어버림 O

\= 메인 함수의 本 Local Variable 지역 변수 값 보존 X

∵ 메인 함수의 지역 변수와 사용자정의 함수의 매개변수가 실제로 "동기화" 되어 있음

i.e.)

어떤 변수가 언제/어떻게 초기화 되었는지 확인할 것이 多

변수 A를 Call by Reference로 실행하는 사용자정의 함수가 여러개 있을때(매개변수가 X, Y, Z)

어떤 사용자정의 함수에서 A 값이 변경되었는지 확인하려면 모든 함수 확인 필요 O

∴ Debugging 단계에서 Error 검출 어려움

※ C++ 기능 O (C 기능 X)
![](https://t9003081320.p.clickup-attachments.com/t9003081320/f23dc817-1bfe-4fbf-8b38-a6e40ac2814b/image.png)
`자료형 &변수명`: Reference 자료형 선언 방법 (E.g. int &X)

**func\_reference\_1.cpp**

```perl
#include <stdio.h>

void swap(int &X, int &Y)          // X = A의 65 + &A, Y = B의 66 + &B
{                                  // 실제로 동기화로 인해 X 주소값 = A 주소값, Y 주소값 = B 주소값
    int temp;                      // 5~8번째줄: X, Y 주소값"은" 유지 + 변수값"만" 변경
    temp = X;                       
    X = Y;
    Y = temp;

    printf("X의 주소: %d\n", &X);
    printf("Y의 주소: %d\n", &Y);
    printf("X의   값: %d\n", X);
    printf("Y의   값: %d\n", Y);
}

int main()
{
    int A, B;
    A = 65;
    B = 66;
    printf("A의 주소: %d\n", &A);
    printf("B의 주소: %d\n", &B);

    printf("swap  전: %d %d\n", A, B);
    swap(A, B);
    printf("swap  후: %d %d\n", A, B);  // 사용자정의 함수의 Reference 자료형으로 인해 메인 함수의 변수와 사용자정의 함수 매개변수가 동기화
                                        // ∴ 메인 함수의 변수값 변경
    
    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/4e62c96e-9df9-4689-ad6f-110c19ac9775/CBR.png)

**func\_reference\_2.cpp**

```perl
// Case #1
#include <stdio.h>

void swap(int X, int Y)            // X = A의 65 + &A, Y = B의 66 + &B
{                                  // 실제로 동기화로 인해 X 주소값 = A 주소값, Y 주소값 = B 주소값
    int temp;                      // 5~8번째줄: X, Y 주소값"은" 유지 + 변수값"만" 변경
    temp = X;                       
    X = Y;
    Y = temp;

    printf("X의 주소: %d\n", &X);
    printf("Y의 주소: %d\n", &Y);
    printf("X의   값: %d\n", X);
    printf("Y의   값: %d\n", Y);
}

int main()
{
    int &A, &B;
    A = 65;
    B = 66;
    // int &A = 65;
    // int &B= 66;

    printf("A의 주소: %d\n", &A);
    printf("B의 주소: %d\n", &B);

    printf("swap  전: %d %d\n", A, B);
    swap(A, B);
    printf("swap  후: %d %d\n", A, B);  // 사용자정의 함수의 Reference 자료형으로 인해 메인 함수의 변수와 사용자정의 함수 매개변수가 동기화
                                        // ∴ 메인 함수의 변수값 변경
    
    return 0;
}
// 결과:  Compiling Error
// 원인:
// 레퍼런스는 상수값으로 초기화할 수 없음
// 레퍼런스는 선언 및 초기화 동시에"만" 가능


// Case #2
#include <stdio.h>

void swap(int X, int Y)            // X = A의 65 + &A, Y = B의 66 + &B
{                                  // 실제로 동기화로 인해 X 주소값 = A 주소값, Y 주소값 = B 주소값
    int temp;                      // 5~8번째줄: X, Y 주소값"은" 유지 + 변수값"만" 변경
    temp = X;                       
    X = Y;
    Y = temp;

    printf("X의 주소: %d\n", &X);
    printf("Y의 주소: %d\n", &Y);
    printf("X의   값: %d\n", X);
    printf("Y의   값: %d\n", Y);
}

int main()
{
    int C, D;
    int &A = C;
    int &B = D;
    C = 65;
    D = 66;
  
    printf("A의 주소: %d\n", &A);
    printf("B의 주소: %d\n", &B);

    printf("swap  전: %d %d\n", A, B);
    swap(A, B);
    printf("swap  후: %d %d\n", A, B);  // 사용자정의 함수의 Reference 자료형으로 인해 메인 함수의 변수와 사용자정의 함수 매개변수가 동기화
                                        // ∴ 메인 함수의 변수값 변경
    
    return 0;
}
// 결과:  A, B 주소값  ≠  X, Y 주소값   →   1) 변수 A, B가 X, Y의 레퍼런스(별명)아 아님  +  2) X, Y는 지역변수이기 때문에 swap이 된 X, Y값은 사용자정의함수 실행 종료후 해제
// 원인:
// 레퍼런스(별명) 선언이 本변수 선언 이후에 해야함
// &A, &B 선언이 X, Y 선언 이후에 해야함


```

※ Reference Data Type 선언 및 초기화

| int A = 10; | O | \- |
| ---| ---| --- |
| int &B = 10; | X | ★ Reference는 상수값으로 초기화 할 수 없음 |
| int &C = A; | O | \- |
| int &D; | X | ★ Reference는 선언 및 초기화 동시에"만" 가능 |
| Reference(별명) 선언은 本 변수 선언 이후에 해야 Reference(별명) 기능이 작동 O |