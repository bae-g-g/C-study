# Auto  vs  Register  vs  Static

## **auto +**
automation duration + no linkage
Local Variable 지역변수
Code BLock 범위"내" 존재
메모리 RAM 관련
지금까지 변수 선언

Code Block 종료시 메모리박스 해제(사용가능 X)
Code Block 내에서 참조가능
초기 초기화값 유지 O
예:
for (int i = 0; i < 5; i++)
{
int X = 5;
X++;
}
i = 0: 메모리박스 X 선언 → 초기값 5 초기화 → 초기값 5 증감 1 = 6 → 메모리박스 X 해제
i = 1: 메모리박스 X 선언 → 초기값 5 초기화 → 초기값 5 증감 1 = 6 → 메모리박스 X 해제
.
.
.
i = 4: 메모리박스 X 선언 → 초기값 5 초기화 → 초기값 5 증감 1 = 6 → 메모리박스 X 해제

Code Block "내"에서 static/register 유형 선언 X → auto 유형(Local Variable 지역변수)이 Default
Code Block "밖"에서 static/register 유형 선언 X → static 유형(Global Variable 전역변수)이 Default

**a\_variable\_auto.c**

```perl
#include <stdio.h>

int main()
{
    if (1)
    {
        int X = 20;                   // auto int X = 20;  automatic duration(블록내 존재 O) + no linkage(블록내 사용 O) → 지역변수(Local Variable):  메모리 RAM 관련 O
        printf("X : %d\n", X);
        printf("X 주소값: %d\n", &X);
    }
    // printf("X : %d\n", X); // Error

    return 0;
}
```

존재 automatic duration: Code Block 내 메모리박스 존재 O → if Code Block 밖 메모리박스 해제 O
사용 no linkage: Code Block 범위내 사용 O → Code Block 범위밖 사용 X

* * *

## **register +**
automation duration + no linkage
Local Variable 지역변수
Code BLock 범위"내" 존재
레지스터 CPU 관련 → 주소값(메모리박스 관련) 참조 X
지금까지 변수 선언

**b\_variable\_register.c**

```perl
#include <stdio.h>

int main()
{
    if (1)
    {
        register int X = 20;            // auto int X = 20;  automatic duration(블록내 존재 O) + no Linkage(블록내 사용 O) → 지역변수(Local Variable):  레지스터 CPU 관련 O
        printf("X: %d\n", X);
        // printf("X 주소값: %d\n", &X);  // Error   ∵ 레지스터 CPU 관련 O (메모리 RAM 관련 X)
    }

    // printf("X : %d\n", X); // Error

    return 0;
}
```

* * *

## **static +**
※ static Global Variable 전역변수 & Static Variable 정적변수는 특정값 초기화하지 않으면 0 초기화

```perl
#include <stdio.h>

int main ()
{
    static int A, B, C, D, E, F, G, H, I, J, K, L, M, N, O, P, Q, R, S, T, U, V, W, X, Y, Z;
    
    printf("%d\n%d\n%d\n%d\n%d\n%d\n%d\n%d\n%d\n%d\n%d\n%d\n%d\n%d\n%d\n%d\n%d\n%d\n%d\n%d\n%d\n%d\n%d\n%d\n%d\n%d\n", A, B, C, D, E, F, G, H, I, J, K, L, M, N, O, P, Q, R, S, T, U, V, W, X, Y, Z);
   
    return 0;
}
```

※ static Global Variable 전역변수 & Static Variable 정적변수는 Compiling 동안 "한번만" 초기화

## **static +**
static duration + internal linkage
Global Variable 전역변수 (변수 앞에 static 선언 생략 → 기본값 static)
Code Block 범위"밖" 존재
메모리 RAM 관련

프로그램 종료시 메모리박스 해제(사용가능 X) + 파일전체내 참조가능 O
초기 초기화값 유지 X

**c\_variable\_static\_1.c**

```perl
// Approach 1:  변수 + 전역변수(Global Variable)
#include <stdio.h>

int X = 20;                      // static int X = 20;  static duration(파일내 존재 O) + internal linkage(파일내 사용 O) → 전역변수(Global Variable):  메모리 RAM 관련 O

void temp()
{
    X += 1;
    printf("X: %d\n", X);
    printf("X 주소값: %d\n", &X);
}

int main()
{
    if (1)
    {
        printf("X: %d\n", X);
        printf("X 주소값: %d\n", &X);
    }

    temp();
    printf("X: %d\n", X);
    printf("X 주소값: %d\n", &X);

    return 0;
}

// Approach 2: 함수 + 지역변수(Local Variable)
#include <stdio.h>

int temp(int Y)                  
{
    Y += 1;
    printf("Y: %d\n", Y);
    printf("Y 주소값: %d\n", &Y);

    return Y;
}

int main()
{
    int X = 20;               

    if (1)
    {
        printf("X: %d\n", X);
        printf("X 주소값: %d\n", &X);
    }

    X = temp(X);                // 48번째줄 까지 X = 20,  50번째줄 함수 실행  →  31번째줄 Y 초기화 할때 X의 값 20만 초기화(메모리박스 X는 이동 X) 
                                // 42번째줄 X의 주소값과  31번째줄 Y의 주소값은 상이 
    printf("X: %d\n", X);
    printf("X 주소값: %d\n", &X);

    return 0;
}
```

## **static +**
static duration + no linkage
Static Variable 정적변수
Code Block 범위"내" 존재
메모리 RAM 관련

프로그램 종료시 메모리박스 해제(사용가능 X) + Code Block내 참조가능 O
초기 초기화값 유지 X
예:
for (int i = 0; i < 5; i++)
{
static int X = 5;
X++;
}
반복마다 메모리박스 선언 X
(반복시 초기 1번 선언 & 메모리박스 유지)
→ 처음 초기화 반복 X
(선언시 새롭게 초기화)
→ 메모리박스 해제 X
(프로그램 종료시 해제 O)
i = 0: 메모리박스 X 선언 → 초기값 5 초기화 → 초기값 5 증감 1 = 6
i = 1: 초기값 6 증감 1 = 7
.
.
.
i = 4: 초기값 6 증감 1 = 10 → 메모리박스 X 해제

**c\_variable\_static\_2.c**

```plain
// Approach 1:  변수 + 정적변수(Static Variable) → Error Code X
#include <stdio.h>

void temp()
{
    static int X = 20;                 // static duration(파일내 존재 O) + no Linkage(블록내 사용 O) → 정적변수(static variable):  메모리 RAM 관련 O
                                       // 반복시 20으로 초기화 X   ∵ Compling Time(exe File 생성)시 1회 초기화 O → Run Time(exe File 실행)시 초기화 X  
    X++;
    printf("X: %d\n", X);
    printf("X 주소값 %d\n", &X);
}

int main()
{
    for (int i = 0; i < 3; i++)
    {
        temp();
    }

    for (int i = 0; i < 3; i++)
    {
        static int Y = 10;
        Y += 1;
        printf("Y: %d\n", Y);
        printf("Y 주소값 %d\n", &Y);
    }
    // printf("X: %d\n", X);        // Error
    // printf("X 주소값 %d\n", &X);  // Error
    // printf("Y: %d\n", Y);        // Error
    // printf("Y 주소값 %d\n", &Y);  // Error
    return 0;
}

// Approach 2:  함수 + 정적변수(Static Variable) → Error Code O
#include <stdio.h>

int temp(int Y)
{
    static int Z = Y;                 // 함수 매개변수 Y(auto int)를 정적변수(Static Variable) Z에 초기화 불가 
                                      // 1) 37번째줄 int Y 선언시 정적변수(Static Variable) 아닌 변수(auto int) 선언 → 정적변수(Static Variable) 자료형에 초기화 X
                                      // 2) 정적변수(Static Variable) Compling Time(exe File 생성)시 1회 초기화 O → Run Time(exe File 실행)시 초기화 X  
                                      // ∴  Compling Time(exe File 생성)시 39번째줄 Z에 초기화할 Y값 없음 → Error 발생 
    Z++;
    printf("Z: %d\n", Z);
    printf("Z 주소값 %d\n", &Z);
    return Z;
}

int main()
{
    int X = 20;

    for (int i = 0; i < 3; i++)
    {
        X = temp(X);
    }

    for (int i = 0; i < 3; i++)
    {
        static int Z = 10;           // 60번째줄 변수 Z는 39번째줄 변수 Z와 다름
                                     // 60번째줄 변수 Z는 39번째줄 변수 Z와 주소값 다름
        Z += 1;
        printf("Z : %d\n", Z);
        printf("Z 주소값 %d\n", &Z);
    }
    printf("X: %d\n", X);       
    printf("X 주소값 %d\n", &X);  
    // printf("Z: %d\n", Z);        // Error
    // printf("Z 주소값 %d\n", &Z);  // Error
    return 0;
}

// Approach 2:  함수 + 정적변수(Static Variable) → Error Code O
#include <stdio.h>

int temp(static int Y)             // 1) 90번째줄 int X 선언시 정적변수(Static Variable) 아닌 변수(auto int) 선언 → 정적변수(Static Variable) 자료형에 초기화 X
                                   // 2) 정적변수(Static Variable) Compling Time(exe File 생성)시 1회 초기화 O → Run Time(exe File 실행)시 초기화 X  
                                   //    94번째줄 함수실행으로 X = 20이 76번째줄 static int Y에 초기화되는 건 Run Time(exe File 실행)시
                                   // ∴  Compling Time(exe File 생성)시 76번째줄 Y에 초기화할 값 없음 → Error 발생 
{
    Y = 20;                 
    Y++;
    printf("Y: %d\n", Y);
    printf("Y 주소값 %d\n", &Y);
    return Y;
}

int main()
{
    int X = 20;

    for (int i = 0; i < 3; i++)
    {
        X = temp(X);                 
    }

    for (int i = 0; i < 3; i++)
    {
        static int Y = 10;           // 99번째줄 변수 Y는 76번째줄 변수 Y와 다름
                                     // 99번째줄 변수 Y는 76번째줄 변수 Y의 주소값 다름
        Y += 1;
        printf("Y: %d\n", Y);
        printf(" 주소값 %d\n", &Y);
    }
    printf("X : %d\n", X);       
    printf("X 주소값 %d\n", &X);  
    // printf("Y : %d\n", Y);       // Error
    // printf("Y 주소값 %d\n", &Y);  // Error
    return 0;
}


// Approach 3:  함수 + 정적변수(Static Variable) → Error Code O
#include <stdio.h>

int temp(static int Y)             // 1) 130번째줄 int X 선언시 정적변수(Static Variable) 아닌 변수(auto int) 선언 → 정적변수(Static Variable) 자료형에 초기화 X
                                   // 2) 정적변수(Static Variable) Compling Time(exe File 생성)시 1회 초기화 O → Run Time(exe File 실행)시 초기화 X  
                                   //    134번째줄 함수실행으로 X = 20이 116번째줄 static int Y에 초기화되는 건 Run Time(exe File 실행)시
                                   // ∴  Compling TimeTime(exe File 생성)시 116번째줄 Y에 초기화할 값 없음 → Error 발생 
{
    Y = 20;                 
    Y++;
    printf("Y: %d\n", Y);
    printf("Y 주소값 %d\n", &Y);
    return Y;
}

int main()
{
    int X;

    for (int i = 0; i < 3; i++)
    {
        X = temp(20);                 
    }

    for (int i = 0; i < 3; i++)
    {
        static int Y = 10;           // 139번째줄 변수 Y는 116번째줄 변수 Y와 다름
                                     // 139번째줄 변수 Y는 116번째줄 변수 Y의 주소값 다름
        Y += 1;
        printf("Y: %d\n", Y);
        printf(" 주소값 %d\n", &Y);
    }
    printf("X : %d\n", X);       
    printf("X 주소값 %d\n", &X);  
    // printf("Y : %d\n", Y);       // Error
    // printf("Y 주소값 %d\n", &Y);  // Error
    return 0;
}

// ∴ C언어에서 정적변수(Static Variable) 사용 빈도 낮음
```

※ 정적변수 자료형 O ≠ 정적변수 자료형 X: 자료형 상이
∴ 초기화 X

```cpp
#include <stdio.h>

int function (int A)
{
    static int B = A;
    B++;
    return B;
}

int main ()
{
    int X = 20;
    int Y = function(Y);
    return 0;
}
```

※ 정적변수 자료형 Compling Time(exe File 생성)시 1회 초기화 O
사용자정의 함수의 매개변수에 초기화되는 시점은 Run Time(exe File 실행)시
∴ 사용자정의 함수의 매개변수가 정적변수 자료형 O → 초기화 X

```cpp
#include <stdio.h>

int function (static int A)
{
    A++;
    return A;
}

int main ()
{
    static int X = 20;
    static int Y = function(X);
    return 0;
}
```

* * *

## **auto + && static +**

**d\_variable\_auto\_static.c**
결제 횟수 / 총액 측정 프로그램

```cpp
// Approach 1:  함수 + 정적변수(Static Variable) → Error Code X
#include <stdio.h>

void payment(int receive_money)    // 23번째줄 함수실행 → 4번째줄 money = 100, 200, 500 초기화 O
{                                  // 정적변수(Static Variable) Compling (exe File 생성)시 1회 초기화 O → Run Time(exe File 실행)시 초기화 X  
    static int payment_count = 0;  // 함수 내에서 static 변수를 초기화 O → Compling (exe File 생성)시 1회 초기화 O 
    static int payment_money = 0;  // 함수 내에서 static 변수를 초기화 O → Compling (exe File 생성)시 1회 초기화 O 
                                   

    payment_count += 1;
    payment_money += money;

    printf("현재 총 결제 횟수는 %d, 총 결제 금액은 %d입니다.\n", payment_count, payment_money);
}

int main()
{
    int input_money;

    for (int i = 0; i < 3; i++)
    {
        scanf("%d", &input_money);   // 100, 200, 500 초기화
        payment(input_money);
    }

    return 0;
}


// Approach 2:  함수 + 전역변수(Global Variable) → Error Code X
#include <stdio.h>
   
int payment_count = 0;               // static 변수와 달리 함수실행시 계속 0으로 초기화
int payment_money = 0;               // static 변수와 달리 함수실행시 계속 0으로 초기화

void payment(int each_money)
{                                  
    // int payment_count = 0;        // static 변수와 달리 함수실행시 계속 0으로 초기화
    // int payment_money = 0;        // static 변수와 달리 함수실행시 계속 0으로 초기화

    payment_count += 1;
    payment_money += each_money;

    printf("현재 총 결제 횟수는 %d, 총 결제 금액은 %d입니다.\n", payment_count, payment_money);
}

int main()
{
    int input_money;
    
    for (int i = 0; i < 3; i++)
    {
        scanf("%d", &input_money);   // 100, 200, 500 초기화
        payment(input_money);
    }

    return 0;
}


// Approach 3-1:  함수 1개 + 지역변수(Local Variable) → Error Code O
#include <stdio.h>
         
void payment(int each_money, int count, int sum_money)
{                                  
    count += 1;
    sum_money += each_money;
    printf("현재 총 결제 횟수는 %d, 총 결제 금액은 %d입니다.\n", count, sum_money);
}

int main()
{
    int input_money;
    int payment_count = 0;        
    int payment_money = 0; 
    
    for (int i = 0; i < 3; i++)
    {
        scanf("%d", &input_money);                           // 100, 200, 500 초기화
        payment(input_money, payment_count, payment_money);  // 반복시 계속 payment_count, payment_money = 0
    }

    return 0;
}

// Approach 3-2A:  함수 2개 + 지역변수(Local Variable) → Error Code X
#include <stdio.h>

int sum_count(int count)
{                                  
    count += 1;
    printf("현재 총 결제 횟수는 %d ", count);
    return count;
}

int sum_money(int each_money, int sum_money)
{                                  
    sum_money += each_money;
    printf("총 결제 금액은 %d입니다.\n", sum_money);
    return sum_money;
}

int main()
{
    int input_money;
    int payment_count = 0;        
    int payment_money = 0; 
    
    for (int i = 0; i < 3; i++)
    {
        scanf("%d", &input_money);                           // 100, 200, 500 초기화
        payment_count = sum_count(payment_count);   
        payment_money = sum_money(input_money, payment_money);
        
    }

    return 0;
}

// Approach 3-2B:  함수 3개 + 지역변수(Local Variable) → Error Code X
#include <stdio.h>

int sum_count(int count)
{                                  
    count += 1;
    return count;
}

int sum_money(int each_money, int sum_money)
{                                  
    sum_money += each_money;
    return sum_money;
}

void sum_print(int count, int sum_money)
{
    printf("현재 총 결제 횟수는 %d, 총 결제 금액은 %d입니다.\n", count, sum_money);
}

int main()
{
    int input_money;
    int payment_count = 0;        
    int payment_money = 0; 
    
    for (int i = 0; i < 3; i++)
    {
        scanf("%d", &input_money);                           // 100, 200, 500 초기화
        payment_count = sum_count(payment_count);   
        payment_money = sum_money(input_money, payment_money);
        sum_print(payment_count, payment_money);
        
    }

    return 0;
}
```