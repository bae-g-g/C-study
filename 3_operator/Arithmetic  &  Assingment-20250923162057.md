# Arithmetic  &  Assingment

## **Arithmetic Operator 산술 연산자**

| + | 좌항 '더하기' 우항 | A + B |
| ---| ---| --- |
| \- | 좌항 '빼기' 우항 | A - B |
| \* | 좌항 '곱하기' 우항 | A \* B |
| / | 좌항 '나누기' 우항 | A / B |
| % | 좌항 나누기 우항 '나머지' | A % B |
| ++ | 변수값 1 증가 | A++ or ++A |
| \-- | 변수값 1 감소 | A-- or --A |

## **Assignment Operator 대입 연산자**

| \= | 우항 → 좌항 대입 | A = B: A ← B |
| ---| ---| --- |
| += | 좌항 '더하기' 우항 → 좌항 대입 | A += B: A = A + B |
| \-= | 좌항 '빼기' 우항 → 좌항 대입 | A -= B: A = A - B |
| \*= | 좌항 '곱하기' 우항 → 좌항 대입 | A \*= B: A = A \* B |
| /= | 좌항 '나누기' 우항 → 좌항 대입 | A /= B: A = A / B |
| %= | 좌항 나누기 우항 '나머지' → 좌항 대입 | A %= B: A = A % B |

컴퓨터 연산
CPU 레지스트리에서 + - & /% 연산: 0 → 1 변환 & 1 → 0 변환'만'으로 수행

### **Example)**

**opt\_aa\_1.c**

```cpp
#include <stdio.h>

// 선언 '동시' 초기화: +-*/%
int main()
{
    int A = 7;            // 정수자료형 7 (4 Bytes) → 선언 문자자료형 크기(4 Bytes) 만큼 입력/저장
    int B = 3;            // 정수자료형 3 (4 Bytes) → 선언 문자자료형 크기(4 Bytes) 만큼 입력/저장
    int C[3] = {2, 4, 6}; // 정수자료형 2, 4, 6 (4 Bytes) → 선언 문자자료형 크기(4 Bytes) 만큼 각각 입력/저장
    int D[3] = {3, 6, 9}; // 정수자료형 3, 6, 9 (4 Bytes) → 선언 문자자료형 크기(4 Bytes) 만큼 각각 입력/저장

    int L = A + B;        // 10진수 7(2진수 00000000  00000000  00000000  00000111) + 10진수 3(2진수 00000000  00000000  00000000  00000011) = 10진수 10(2진수  00000000  00000000  00000000  00001010)
    int M = A - B;        // 10진수 7(2진수 00000000  00000000  00000000  00000111) - 10진수 3(2진수 00000000  00000000  00000000  00000011) = 10진수  4(2진수  00000000  00000000  00000000  00000100)
    int N = A * B;        
    int O = A / B;
    int P = A % B;

    int V = C[0] + C[1];
    int W = C[2] - D[2];
    int X = D[1] * C[0];
    int Y = C[2] / D[1];
    int Z = D[2] % C[2];

    int Q = (A + C[0] * B / D[1]) % B;

    // 선언한 자료형크기 만큼 각각 정수 1개 출력
    printf("%d  %d  %d  %d  %d\n", L, M, N, O, P);
    printf("%d  %d  %d  %d  %d\n", A + B, A - B, A * B, A / B, A % B);
    printf("%d  %d  %d  %d  %d\n", V, W, X, Y, Z);
    printf("%d  %d  %d  %d  %d\n", C[0] + C[1], C[2] - D[2], D[1] * C[0], C[2] / D[1], D[2] % C[2]);

    printf("%d\n", Q);
    printf("%d\n", (A + C[0] * B / D[1]) % B);

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/2798f3bc-95e7-4e06-8a7e-456fbd3e7282/Picture3.png)

**opt\_aa\_2.c**

```cpp
#include <stdio.h>

// 선언 '후' 초기화: +-*/%
// Case 1
int main()
{
    int A; 
    int B;

    // 선언 '후' 초기화 X 상태 → 메모리박스 A, B내 \0=null or 쓰레기값 존재 → if \0=null 존재 = 나누기 0 연산 X → 나머지 연산 X
    int L = A + B;
    int M = A - B;
    int N = A * B;
    int O = A / B;               // 주석처리
    int P = A % B;               // 주석처리
    int Q = (A + B * A / B) % A; // 주석처리

    printf("---Input---\n");
    scanf("%d", &A);             // 예: %d 정수자료형 7(4 Bytes) A 주소값(&)을 시작으로 입력/저장
    scanf("%d", &B);             // 예: %d 정수자료형 3(4 Bytes) B 주소값(&)을 시작으로 입력/저장

    printf("---Output---\n");
    // 선언한 자료형크기 만큼 각각 정수 1개 출력
    printf("%d  %d  %d\n", L, M, N);
    printf("%d  %d  %d  %d  %d\n", L, M, N, O, P);                     // 주석처리
    printf("%d  %d  %d\n", A + B, A - B, A * B);
    printf("%d  %d  %d  %d  %d\n", A + B, A - B, A * B, A / B, A % B); // 주석처리
    printf("%d\n", Q);                                                 // 주석처리
    printf("%d\n", (A + B * A / B) % A);                               // 주석처리

    return 0;
}

// Case 2
int main()
{
    int A;
    int B;

    printf("---Input---\n");
    scanf("%d", &A);             // 예: %d 정수자료형 7(4 Bytes) A 주소값(&)을 시작으로 입력/저장
    scanf("%d", &B);             // 예: %d 정수자료형 3(4 Bytes) B 주소값(&)을 시작으로 입력/저장

    // 선언 '후' 초기화 O 상태
    int L = A + B;
    int M = A - B;
    int N = A * B;
    int O = A / B;
    int P = A % B;
    int Q = (A + B * A / B) % A;

    printf("---Output---\n");
    // 선언한 자료형크기 만큼 각각 정수 1개 출력
    printf("%d  %d  %d  %d  %d\n", L, M, N, O, P);
    printf("%d  %d  %d  %d  %d\n", A + B, A - B, A * B, A / B, A % B);
    printf("%d\n", Q);
    printf("%d\n", (A + B * A / B) % A);

    return 0;
}


```

![](https://t9003081320.p.clickup-attachments.com/t9003081320/3403fd03-0fd4-42d2-a6fe-bda1c87a7c1e/Picture4.png)

**opt\_aa\_3.c**

```cpp
#include <stdio.h>

// 선언 '동시' 초기화: +-*/%
int main()
{
    float A = 0.5;                       // 소수자료형  0.5 (4 Bytes) → 선언 문자자료형 크기(4 Bytes) 만큼 입력/저장
    float B = 0.25;                      // 소수자료형 0.25 (4 Bytes) → 선언 문자자료형 크기(4 Bytes) 만큼 입력/저장
    float C[3] = {0.5, 0.125, 0.03125};  // 소수자료형  0.5, 0.125, 0.03125 (4 Bytes) → 선언 문자자료형 크기(4 Bytes) 만큼 각각 입력/저장
    float D[3] = {0.25, 0.625, 8.625};   // 소수자료형 0.25, 0.625,   8.625 (4 Bytes) → 선언 문자자료형 크기(4 Bytes) 만큼 각각 입력/저장

    float L = A + B;        
    float M = A - B;        
    float N = A * B;
    float O = A / B;
    // float P = A % B; // 소수는 나머지 계산 X

    float V = C[0] + C[1];
    float W = C[2] - D[2];
    float X = D[1] * C[0];
    float Y = C[2] / D[1];
    // float Z = D[2] % C[2]; // 소수는 나머지 계산 X

    float Q = (A + C[0] * B / D[1]);

    // 선언한 자료형크기 만큼 각각 소수 1개 출력
    printf("%f  %f  %f  %f\n", L, M, N, O);
    printf("%f  %f  %f  %f\n", A + B, A - B, A * B, A / B);
    printf("%f  %f  %f  %f\n", V, W, X, Y);
    printf("%f  %f  %f  %f\n", C[0] + C[1], C[2] - D[2], D[1] * C[0], C[2] / D[1]);

    printf("%f\n", Q);
    printf("%f\n", (A + C[0] * B / D[1]));

    return 0;
}


```

**opt\_aa\_4.c**

```cpp
#include <stdio.h>

// 선언 '후' 초기화: +-*/%
int main()
{
    float A;               
    float B;
    printf("---Input---\n");
    scanf("%f", &A);             // 예: %f 정수자료형  0.5(4 Bytes) A 주소값(&)을 시작으로 입력/저장
    scanf("%f", &B);             // 예: %f 정수자료형 0.25(4 Bytes) B 주소값(&)을 시작으로 입력/저장              

    float L = A + B;        
    float M = A - B;        
    float N = A * B;
    float O = A / B;
    // float P = A % B; // 소수는 나머지 계산 X

    printf("---Output---\n");
    // 선언한 자료형크기 만큼 각각 정수 1개 출력
    printf("%f  %f  %f  %f\n", L, M, N, O);
    printf("%f  %f  %f  %f\n", A + B, A - B, A * B, A / B); 

    return 0;
}


```

**opt\_aa\_5.c**

```cpp
#include <stdio.h>
// scanf 사용 X: 변수 1개

// Case 1-1
int main ()
{
    int X = 7;              // 정수자료형 7 (4 Bytes) → 선언 문자자료형 크기(4 Bytes) 만큼 입력/저장
    int Y = 9;              // 정수자료형 9 (4 Bytes) → 선언 문자자료형 크기(4 Bytes) 만큼 입력/저장
 
    printf("---Output X---\n");
    printf("%d\n", X);      // 입력/저장된 7 출력

    printf("---Increment & Decrement X (1)---\n");
    ++X;                    // X + 1(정수 7 + 1 = 8 상태)
    printf("%d\n", X);      // 8 출력

    printf("---Increment & Decrement X (2)---\n");
    X--;                    // X - 1(정수 8 - 1 = 7 상태)
    printf("%d\n", X);      // 7 출력

    printf("---Increment & Decrement X (3)---\n");
    printf("%d\n", X++);    // X = 7 상태 출력 '후' X + 1  (X = 8 상태):  7 출력
    printf("%d\n", ++X);    // X + 1(정수 8 + 1) '후' 출력 (X = 9 상태):  9 출력
    printf("%d\n", X--);    // X = 9 상태 출력 '후' X - 1  (X = 8 상태):  9 출력
    printf("%d\n", --X);    // X - 1(정수 8 - 1) '후' 출력 (X = 7 상태):  7 출력

    printf("---Output X & Y---\n");
    printf("%d\n", X);      // 입력/저장된 7 출력
    printf("%d\n", Y);      // 입력/저장된 9 출력

    printf("---Assingment X & Y---\n");
    printf("%d\n", X += Y); // X = X( =7) + Y = 16:  16 출력
    printf("%d\n", X -= Y); // X = X(=16) - Y =  7:   7 출력
    printf("%d\n", X *= Y); // X = X( =7) * Y = 63:  63 출력
    printf("%d\n", X /= Y); // X = X(=63) / Y =  Y:   7 출력
    printf("%d\n", X %= Y); // X = X( =7) % Y =  9:   7 출력

    return 0;      
}

// Case 1-2
int main ()
{
    int X = 7;                // 정수자료형 7 (4 Bytes) → 선언 문자자료형 크기(4 Bytes) 만큼 입력/저장

    int Y = X++;              // X방식(TEMP O): X = 7 상태 Y에 초기화 '후' X + 1    (X = 8 상태):  7 출력  ∵ 8상태 전 같은줄에 Y에 초기화
    int Z = ++X;              // Y방식(TEMP X): X + 1(정수 8 + 1) '후' Z에 9 초기화 (X = 9 상태):  9 출력
    printf("---Increment & Decrement X → Y, Z (1)---\n");
    printf("%d  %d\n", Y, Z); // X++(TEMP O) & ++X(TEMP X) 연산 후 Y, Z 변수에 초기화 된 값 출력 → X++(TEMP O) & ++X(TEMP X) 연산 실질적 작동 But 각각의 줄(46, 47번째 줄) 단일 연산으로 인해 표면적으로 알수 없음

    printf("---Increment & Decrement X (2)---\n");
    printf("%d\n", X++);      // X = 9 상태 초기화  '후' X + 1  (X = 10 상태):  9 출력
    printf("%d\n", ++X);      // X + 1(정수 10 + 1) '후' 초기화 (X = 11 상태): 11 출력

    int I = 7;
    I++;                      // X방식(TEMP O): I = 7 상태 초기화  '후' I + 1       (I = 8 상태):  8 출력  ∵ 8상태 후 다음줄에 J에 초기화
    int J = I;
    ++I;                      // Y방식(TEMP X): I + 1(정수 8 + 1) '후' I = 9 초기화 (I = 9 상태):  9 출력
    int K = I;
    printf("---Increment & Decrement I → J, K (3)---\n");
    printf("%d  %d\n", J, K); // I++(TEMP O) & ++I(TEMP X) 연산 후 J, K 변수에 초기화 된 값 출력 → I++(TEMP O) & ++I(TEMP X) 연산 실질적 작동 But 각각의 줄(56, 57번째 줄) 단일 연산으로 인해 표면적으로 알수 없음

    int A = 7;                // 정수자료형 7 (4 Bytes) → 선언 문자자료형 크기(4 Bytes) 만큼 입력/저장
    int B = 9;                // 정수자료형 9 (4 Bytes) → 선언 문자자료형 크기(4 Bytes) 만큼 입력/저장

    int C = A += B;           // A = A( =7) + B = 16 → C에 초기화
    int D = A -= B;           // A = A(=16) - B =  7 → D에 초기화 
    int E = A *= B;           // A = A( =7) * B = 63 → E에 초기화 
    int F = A /= B;           // A = A(=63) / B =  7 → F에 초기화
    int G = A %= B;           // A = A( =7) % B =  7 → G에 초기화 

    printf("---Assignment A & B---\n");
    printf("%d\n", C);        // 16 출력
    printf("%d\n", D);        //  7 출력
    printf("%d\n", E);        // 63 출력
    printf("%d\n", F);        //  7 출력
    printf("%d\n", G);        //  7 출력

    return 0;
}


```

**opt\_aa\_6.c**

```cpp
#include <stdio.h>
// scanf 사용 X: 배열

// Case 1-1
int main ()
{
    int X[3] = {2, 7, 8};              
    int Y[3] = {0, 3, 9};             
 
    printf("---Output X---\n");
    printf("%d\n", X[1]);         // 입력/저장된 7 출력

    printf("---Increment & Decrement X (1)---\n");
    ++X[1];                       // X[1] + 1(정수 7 + 1 = 8 상태)
    printf("%d\n", X[1]);         // 8 출력

    printf("---Increment & Decrement X (2)---\n");
    X[1]--;                       // X[1] - 1(정수 8 - 1 = 7 상태)
    printf("%d\n", X[1]);         // 7 출력

    printf("---Increment & Decrement X (3)---\n");
    printf("%d\n", X[1]++);       // X[1] = 7 상태 출력 '후' X[1] + 1  (X[1] = 8 상태):  7 출력
    printf("%d\n", ++X[1]);       // X[1] + 1(정수 8 + 1) '후' 출력 (X[1] = 9 상태):  9 출력
    printf("%d\n", X[1]--);       // X[1] = 9 상태 출력 '후' X[1] - 1  (X[1] = 8 상태):  9 출력
    printf("%d\n", --X[1]);       // X[1] - 1(정수 8 - 1) '후' 출력 (X[1] = 7 상태):  7 출력

    printf("---Output X & Y---\n");
    printf("%d\n", X[1]);         // 입력/저장된 7 출력
    printf("%d\n", Y[2]);         // 입력/저장된 9 출력

    printf("---Assingment X & Y---\n");
    printf("%d\n", X[1] += Y[2]); // X[1] = X[1]( =7) + Y[2] = 16:  16 출력
    printf("%d\n", X[1] -= Y[2]); // X[1] = X[1](=16) - Y[2] =  7:   7 출력
    printf("%d\n", X[1] *= Y[2]); // X[1] = X[1]( =7) * Y[2] = 63:  63 출력
    printf("%d\n", X[1] /= Y[2]); // X[1] = X[1](=63) / Y[2] =  Y:   7 출력
    printf("%d\n", X[1] %= Y[2]); // X[1] = X[1]( =7) % Y[2] =  9:   7 출력

    return 0;      
}

// Case 1-2
int main ()
{
    int X[3] = {2, 7, 8};                  

    int Y = X[1]++;              // X방식(TEMP O): X[1] = 7 상태 Y에 초기화 '후' X + 1    (X[1] = 8 상태):  7 출력  ∵ 8상태 전 같은줄에 Y에 초기화
    int Z = ++X[1];              // Y방식(TEMP X): X[1] + 1(정수 8 + 1) '후' Z에 9 초기화 (X[1] = 9 상태):  9 출력
    printf("---Increment & Decrement X → Y, Z (1)---\n");
    printf("%d  %d\n", Y, Z);    // X[1]++(TEMP O) & ++X[1](TEMP X) 연산 후 Y, Z 변수에 초기화 된 값 출력 → X[1]++(TEMP O) & ++X[1](TEMP X) 연산 실질적 작동 But 각각의 줄(46, 47번째 줄) 단일 연산으로 인해 표면적으로 알수 없음

    printf("---Increment & Decrement X (2)---\n");
    printf("%d\n", X[1]++);      // X[1] = 9 상태 초기화  '후' X[1] + 1  (X[1] = 10 상태):  9 출력
    printf("%d\n", ++X[1]);      // X[1] + 1(정수 10 + 1) '후' 초기화    (X[1] = 11 상태): 11 출력

    int I[3] = {2, 7, 8};  
    I[1]++;                      // X방식(TEMP O): I[1] = 7 상태 초기화 '후' I[1] + 1        (I[1] = 8 상태):  8 출력  ∵ 8상태 후 다음줄에 J에 초기화
    int J = I[1];
    ++I[1];                      // Y방식(TEMP X): I[1] + 1(정수 8 + 1) '후' I[1] = 9 초기화 (I[1] = 9 상태):  9 출력
    int K = I[1];
    printf("---Increment & Decrement I → J, K (3)---\n");
    printf("%d  %d\n", J, K);    // I[1]++(TEMP O) & ++I[1](TEMP X) 연산 후 J, K 변수에 초기화 된 값 출력 → I[1]++(TEMP O) & ++I[1](TEMP X) 연산 실질적 작동 But 각각의 줄(56, 57번째 줄) 단일 연산으로 인해 표면적으로 알수 없음

    int A[3] = {2, 7, 8};                  
    int B[3] = {0, 4, 9};        

    int C = A[1] += B[2];        // A[1] = A[1]( =7) + B[2] = 16 → C에 초기화
    int D = A[1] -= B[2];        // A[1] = A[1](=16) - B[2] =  7 → D에 초기화 
    int E = A[1] *= B[2];        // A[1] = A[1]( =7) * B[2] = 63 → E에 초기화 
    int F = A[1] /= B[2];        // A[1] = A[1](=63) / B[2] =  7 → F에 초기화
    int G = A[1] %= B[2];        // A[1] = A[1]( =7) % B[2] =  7 → G에 초기화 

    printf("---Assignment A & B---\n");
    printf("%d\n", C);           // 16 출력
    printf("%d\n", D);           // -7 출력
    printf("%d\n", E);           // 63 출력
    printf("%d\n", F);           //  7 출력
    printf("%d\n", G);           //  7 출력

    return 0;
}


```

**opt\_aa\_7.c**

```cpp
#include <stdio.h>
// scanf 사용 O: 변수 1개

// Case 1-1
int main ()
{
    int X;              
    int Y;
    printf("---input X & Y---\n"); 
    scanf("%d", &X);           // 예: 7 입력/저장[%d 정수자료형 7(4 Bytes) X 주소값(&)을 시작으로 입력/저장]
    scanf("%d", &Y);           // 예: 9 입력/저장[%d 정수자료형 7(4 Bytes) Y 주소값(&)을 시작으로 입력/저장]   
 
    printf("---Output X---\n");
    printf("%d\n", X);         // 입력/저장된 7 출력

    printf("---Increment & Decrement X (1)---\n");
    ++X;                       // X + 1(정수 7 + 1 = 8 상태)
    printf("%d\n", X);         // 8 출력

    printf("---Increment & Decrement X (2)---\n");
    X--;                       // X - 1(정수 8 - 1 = 7 상태)
    printf("%d\n", X);         // 7 출력

    printf("---Increment & Decrement X (3)---\n");
    printf("%d\n", X++);       // X = 7 상태 출력 '후' X + 1  (X = 8 상태):  7 출력
    printf("%d\n", ++X);       // X + 1(정수 8 + 1) '후' 출력 (X = 9 상태):  9 출력
    printf("%d\n", X--);       // X = 9 상태 출력 '후' X - 1  (X = 8 상태):  9 출력
    printf("%d\n", --X);       // X - 1(정수 8 - 1) '후' 출력 (X = 7 상태):  7 출력

    printf("---Output X & Y---\n");
    printf("%d\n", X);         // 입력/저장된 7 출력
    printf("%d\n", Y);         // 입력/저장된 9 출력

    printf("---Assingment X & Y---\n");
    printf("%d\n", X += Y);    // X = X( =7) + Y = 16:  16 출력
    printf("%d\n", X -= Y);    // X = X(=16) - Y = -7:   7 출력
    printf("%d\n", X *= Y);    // X = X( =7) * Y = 63:  63 출력
    printf("%d\n", X /= Y);    // X = X(=63) / Y =  Y:   7 출력
    printf("%d\n", X %= Y);    // X = X( =7) % Y =  9:   7 출력

    return 0;      
}

// Case 1-2
int main ()
{
    int X;
    printf("---input X---\n");               
    scanf("%d", &X);          // 예: 7 입력/저장[%d 정수자료형 7(4 Bytes) X 주소값(&)을 시작으로 입력/저장]

    int Y = X++;              // X방식(TEMP O): X = 7 상태 Y에 초기화 '후' X + 1    (X = 8 상태):  7 출력  ∵ 8상태 전 같은줄에 Y에 초기화
    int Z = ++X;              // Y방식(TEMP X): X + 1(정수 8 + 1) '후' Z에 9 초기화 (X = 9 상태):  9 출력
    printf("---Increment & Decrement X → Y, Z (1)---\n");
    printf("%d %d\n", Y, Z);  // X++(TEMP O) & ++X(TEMP X) 연산 후 Y, Z 변수에 초기화 된 값 출력 → X++(TEMP O) & ++X(TEMP X) 연산 실질적 작동 But 각각의 줄(51, 52번째 줄) 단일 연산으로 인해 표면적으로 알수 없음

    printf("---Increment & Decrement X (2)---\n");
    printf("%d\n", X++);      // X = 9 상태 초기화  '후' X + 1  (X = 10 상태):  9 출력
    printf("%d\n", ++X);      // X + 1(정수 10 + 1) '후' 초기화 (X = 11 상태): 11 출력

    int I;
    printf("---input I---\n");               
    scanf("%d", &X);          // 예: 7 입력/저장[%d 정수자료형 7(4 Bytes) X 주소값(&)을 시작으로 입력/저장]
    
    I++;                      // X방식(TEMP O): I = 7 상태 초기화  '후' I + 1       (I = 8 상태):  8 출력  ∵ 8상태 후 다음줄에 J에 초기화
    int J = I;
    ++I;                      // Y방식(TEMP X): I + 1(정수 8 + 1) '후' I = 9 초기화 (I = 9 상태):  9 출력
    int K = I;
    printf("---Increment & Decrement I → J, K (3)---\n");
    printf("%d  %d\n", J, K); // I++(TEMP O) & ++I(TEMP X) 연산 후 J, K 변수에 초기화 된 값 출력 → I++(TEMP O) & ++I(TEMP X) 연산 실질적 작동 But 각각의 줄(64, 66번째 줄) 단일 연산으로 인해 표면적으로 알수 없음

    int A;                
    int B;                
    printf("---input A & B---\n");               
    scanf("%d", &X);          // 예: 7 입력/저장[%d 정수자료형 7(4 Bytes) X 주소값(&)을 시작으로 입력/저장]
    scanf("%d", &Y);          // 예: 9 입력/저장[%d 정수자료형 7(4 Bytes) Y 주소값(&)을 시작으로 입력/저장]

    int C = A += B;           // A = A( =7) + B = 16 → C에 초기화
    int D = A -= B;           // A = A(=16) - B =  7 → D에 초기화 
    int E = A *= B;           // A = A( =7) * B = 63 → E에 초기화 
    int F = A /= B;           // A = A(=63) / B =  7 → F에 초기화
    int G = A %= B;           // A = A( =7) % B =  7 → G에 초기화 

    printf("---Assignment A & B---\n");
    printf("%d\n", C);        // 16 출력
    printf("%d\n", D);        //  7 출력
    printf("%d\n", E);        // 63 출력
    printf("%d\n", F);        //  7 출력
    printf("%d\n", G);        //  7 출력

    return 0;
}


```

**opt\_aa\_8.c**

```cpp
#include <stdio.h>
// scanf 사용 O: 배열

// Case 1-1
int main ()
{
    int X[3];                      
    int Y[3];     
    printf("---input X & Y---\n");
    for (int i = 0; i < 3; i++)
    {
        scanf("%d", &X[i]);       // 예: i = 0 일때 2, i = 1 일때 7, i = 2 일때 8 입력/저장      
    }
    for (int i = 0; i < 3; i++)
    {
    scanf("%d", &Y[i]);           // 예: i = 0 일때 0, i = 1 일때 3, i = 2 일때 9 입력/저장      
    }

    printf("---Output X---\n");
    printf("%d\n", X[1]);         // 입력/저장된 7 출력

    printf("---Increment & Decrement X (1)---\n");
    ++X[1];                       // X[1] + 1(정수 7 + 1 = 8 상태)
    printf("%d\n", X[1]);         // 8 출력

    printf("---Increment & Decrement X (2)---\n");
    X[1]--;                       // X[1] - 1(정수 8 - 1 = 7 상태)
    printf("%d\n", X[1]);         // 7 출력

    printf("---Increment & Decrement X (3)---\n");
    printf("%d\n", X[1]++);       // X[1] = 7 상태 출력 '후' X[1] + 1  (X[1] = 8 상태):  7 출력
    printf("%d\n", ++X[1]);       // X[1] + 1(정수 8 + 1) '후' 출력 (X[1] = 9 상태):  9 출력
    printf("%d\n", X[1]--);       // X[1] = 9 상태 출력 '후' X[1] - 1  (X[1] = 8 상태):  9 출력
    printf("%d\n", --X[1]);       // X[1] - 1(정수 8 - 1) '후' 출력 (X[1] = 7 상태):  7 출력

    printf("---Output X & Y---\n");
    printf("%d\n", X[1]);         // 입력/저장된 7 출력
    printf("%d\n", Y[2]);         // 입력/저장된 9 출력

    printf("---Assingment X & Y---\n");
    printf("%d\n", X[1] += Y[2]); // X[1] = X[1]( =7) + Y[2] = 16:  16 출력
    printf("%d\n", X[1] -= Y[2]); // X[1] = X[1](=16) - Y[2] = -7:   7 출력
    printf("%d\n", X[1] *= Y[2]); // X[1] = X[1]( =7) * Y[2] = 63:  63 출력
    printf("%d\n", X[1] /= Y[2]); // X[1] = X[1](=63) / Y[2] =  Y:   7 출력
    printf("%d\n", X[1] %= Y[2]); // X[1] = X[1]( =7) % Y[2] =  9:   7 출력

    return 0;      
}

// Case 1-2
int main ()
{
    int X[3];
    printf("---input X---\n");
    for (int i = 0; i < 3; i++)
    {
        scanf("%d", &X[i]);      // 예: i = 0 일때 2, i = 1 일때 7, i = 2 일때 8 입력/저장      
    }                  

    int Y = X[1]++;              // X방식(TEMP O): X[1] = 7 상태 Y에 초기화 '후' X + 1    (X[1] = 8 상태):  7 출력  ∵ 8상태 전 같은줄에 Y에 초기화
    int Z = ++X[1];              // Y방식(TEMP X): X[1] + 1(정수 8 + 1) '후' Z에 9 초기화 (X[1] = 9 상태):  9 출력
    printf("---Increment & Decrement X → Y, Z (1)---\n");
    printf("%d  %d\n", Y, Z);    // X[1]++(TEMP O) & ++X[1](TEMP X) 연산 후 Y, Z 변수에 초기화 된 값 출력 → X[1]++(TEMP O) & ++X[1](TEMP X) 연산 실질적 작동 But 각각의 줄(46, 47번째 줄) 단일 연산으로 인해 표면적으로 알수 없음

    printf("---Increment & Decrement X (2)---\n");
    printf("%d\n", X[1]++);      // X[1] = 9 상태 초기화  '후' X[1] + 1  (X[1] = 10 상태):  9 출력
    printf("%d\n", ++X[1]);      // X[1] + 1(정수 10 + 1) '후' 초기화    (X[1] = 11 상태): 11 출력

    int I[3];    
    printf("---input I---\n");
    for (int i = 0; i < 3; i++)
    {
        scanf("%d", &I[i]);       // 예: i = 0 일때 2, i = 1 일때 7, i = 2 일때 8 입력/저장      
    }  

    I[1]++;                      // X방식(TEMP O): I[1] = 7 상태 초기화  '후' I[1] + 1       (I[1] = 8 상태):  8 출력  ∵ 8상태 후 다음줄에 J에 초기화
    int J = I[1];
    ++I[1];                      // Y방식(TEMP X): [1] + 1(정수 8 + 1) '후' I[1] = 9 초기화 (I[1] = 9 상태):  9 출력
    int K = I[1];
    printf("---Increment & Decrement I → J, K (3)---\n");
    printf("%d  %d\n", J, K);    // I[1]++(TEMP O) & ++I[1](TEMP X) 연산 후 J, K 변수에 초기화 된 값 출력 → I[1]++(TEMP O) & ++I[1](TEMP X) 연산 실질적 작동 But 각각의 줄(56, 57번째 줄) 단일 연산으로 인해 표면적으로 알수 없음

    int A[3];                  
    int B[3];
    printf("---input A & B---\n");
    for (int i = 0; i < 3; i++)
    {
        scanf("%d", &A[i]);      // 예: i = 0 일때 2, i = 1 일때 7, i = 2 일때 8 입력/저장      
    }
    for (int i = 0; i < 3; i++)
    {
        scanf("%d", &B[i]);      // 예: i = 0 일때 0, i = 1 일때 4, i = 2 일때 9 입력/저장      
    }        

    int C = A[1] += B[2];        // A[1] = A[1]( =7) + B[2] = 16 → C에 초기화
    int D = A[1] -= B[2];        // A[1] = A[1](=16) - B[2] =  7 → D에 초기화 
    int E = A[1] *= B[2];        // A[1] = A[1]( =7) * B[2] = 63 → E에 초기화 
    int F = A[1] /= B[2];        // A[1] = A[1](=63) / B[2] =  7 → F에 초기화
    int G = A[1] %= B[2];        // A[1] = A[1]( =7) % B[2] =  7 → G에 초기화 

    printf("---Assignment A & B---\n");
    printf("%d\n", C);           // 16 출력
    printf("%d\n", D);           //  7 출력
    printf("%d\n", E);           // 63 출력
    printf("%d\n", F);           //  7 출력
    printf("%d\n", G);           //  7 출력

    return 0;
}


```

**opt\_aa\_9.c**

```cpp
#include <stdio.h>
// 증감연산 한줄 출력 X:  이유 1: OS 차이 → 출력 차이,   이유 2: 가시성 ↓
// scanf 사용 X: 변수 1개
int main()
{
    int A = 5;                             // Y방식(TEMP X: 최종초기화)
    printf("%d  %d  %d\n", A++, A++, A++); // X방식(TEMP O: 각각초기화)
    // Window OS(L ← R):  X방식(TEMP O: 각각초기화)
    // TEMP A2 ← A1 ← A0: 7 ← 6 ← 5 각각 초기화/출력
    // Mac OS(L → R):     X방식(TEMP O: 각각초기화)
    // 5 → 6 → 7

    int B = 5;                             // Y방식(TEMP X: 최종초기화)
    printf("%d  %d  %d\n", ++B, ++B, ++B); // Y방식(TEMP X: 최종초기화)
    // Window OS(L ← R):  Y방식(TEMP X: 최종초기화)
    // 8 ← 7 ← 6: 최종 8 초기화/출력
    // Mac OS(L → R):     X방식(TEMP O: 각각초기화)
    // 6 → 7 → 8
    
    int C = 7;                                      // Y방식(TEMP X: 최종초기화)
    printf("%d  %d  %d  %d\n", C++, ++C, C++, ++C); // 후위연산자: X방식(TEMP O: 각각초기화) + 전위연사자: Y방식(TEMP X: 최종초기화)
    // Window OS(L ← R):  후위연산자: X방식(TEMP O: 각각초기화) + 전위연사자: Y방식(TEMP X: 최종초기화)
    // 1) ++C(TEMP X):  ++(8 상태) → C =  8 초기화   2) E++(TEMP O): C =  8 초기화상태 유지/출력 → ++( 9 상태)
    // 3) ++C(TEMP X): ++(10 상태) → C = 10 초기화   4) E++(TEMP O): C = 10 초기화상태 유지/출력 → ++(11 상태 = 최종상태)
    // ∴  2) C++(TEMP O) = 8 초기화/출력,   4) C++(TEMP O): C = 10 초기화/출력,   1) & 3) ++C(TEMP X): 최종값 '4) C++(TEMP O): C = 11' 초기화/출력
    // ∴  10  11  8  11
    // Mac OS(L → R):     
    // 7 → 9 → 9 → 11
    
    int D = 8;                                                              // Y방식(TEMP X: 최종초기화)
    int E = 9;                                                              // Y방식(TEMP X: 최종초기화)
    printf("%d  %d  %d  %d  %d\n", D += E, D -= E, D *= E, D /= E, D %= E); // Y방식(TEMP X: 최종초기화)
    // Window OS(L ← R):  Y방식(TEMP X: 최종초기화)
    // 0 ← -9 ← 0 ← 0 ← 8: 최종 0 초기화/출력
    // Mac OS(L → R):     X방식(TEMP O: 각각초기화)
    // 17 → 8 → 72 → 8 → 8 

    return 0;
}
// 연산 방식 Image 참조


```

`Window OS`
![](https://t9003081320.p.clickup-attachments.com/t9003081320/0c246df9-0130-4d7e-b341-a1128c8ec6e5/Picture1.png)

**opt\_aa\_10.c**

```cpp
#include <stdio.h>
// 증감연산 한줄 출력 X:  이유 1: OS 차이 → 출력 차이,   이유 2: 가시성 ↓
// scanf 사용 X: 배열
int main()
{
    int A[3] = {3, 5, 8};                              // Y방식(TEMP X: 최종초기화)
    printf("%d  %d  %d\n", A[1]++, A[1]++, A[1]++);    // X방식(TEMP O: 각각초기화)
    // Window OS(L ← R):  X방식(TEMP O: 각각초기화)
    // TEMP A[1]2 ← A[1]1 ← A[1]0: 7 ← 6 ← 5 각각 초기화/출력
    // Mac OS(L → R):     X방식(TEMP O: 각각초기화)
    // 5 → 6 → 7

    int B[3] = {3, 5, 8};                              // Y방식(TEMP X: 최종초기화)
    printf("%d  %d  %d\n", ++B[1], ++B[1], ++B[1]);    // X방식(TEMP O: 각각초기화) ← 本 Y 방식(TEMP 작동 X)
    // Window OS(L ← R):  X방식(TEMP O: 각각초기화)
    // TEMP B[1]2 ← B[1]1 ← B[1]0: 8 ← 7 ← 6 각각 초기화/출력
    // Mac OS(L → R):     X방식(TEMP O: 각각초기화)
    // 6 → 7 → 8

    int C[3] = {3, 7, 8};                                       // Y방식(TEMP X: 최종초기화)
    printf("%d  %d  %d  %d\n", C[1]++, ++C[1], C[1]++, ++C[1]); // 후위연산자: X방식(TEMP O: 각각초기화) + 전위연사자: X방식(TEMP O: 각각초기화) ← 本 Y 방식(TEMP 작동 X)
    // Window OS(L ← R):  후위연산자: X방식(TEMP O: 각각초기화) + 전위연사자: X방식(TEMP O: 각각초기화)
    // 1) ++C(TEMP X): ++ (8 상태) → C =  8 초기화/출력   2) C++(TEMP O): C =  8 초기화상태 유지/출력 → ++( 9 상태)
    // 3) ++C(TEMP X): ++(10 상태) → C = 10 초기화/출력   4) C++(TEMP O): C = 10 초기화상태 유지/출력 → ++(11 상태)
    // ∴  10  10  8  8
    // Mac OS(L → R):
    // 7 → 9 → 9 → 11

    int D[3] = {3, 8, 12};                                                                                // Y방식(TEMP X: 최종초기화)
    int E[3] = {2, 4, 9};                                                                                 // Y방식(TEMP X: 최종초기화)
    printf("%d  %d  %d  %d  %d\n", D[1] += E[2], D[1] -= E[2], D[1] *= E[2], D[1] /= E[2], D[1] %= E[2]); // X방식(TEMP O: 각각초기화)
    // Window OS(L ← R):  X방식(TEMP O: 각각초기화)
    // TEMP D[0]4 ← D[0]3 ← D[0]2 ← D[0]1 ← D[0]0: 0 ← -9 ← 0 ← 0 ← 8 초기화/출력
    // Mac OS(L → R):     X방식(TEMP O: 각각초기화)
    // 17 → 8 → 72 → 8 → 8

    return 0;
}


```

**opt\_aa\_11.c**

```cpp
#include <stdio.h>
// 증감연산 한줄 출력 X:  이유 1: OS 차이 → 출력 차이,   이유 2: 가시성 ↓
// scanf 사용 O: 변수 1개
int main()
{
    int A;
    printf("---input A---\n");                      // 예: 5 입력/저장
    scanf("%d", &A);                                // X방식(TEMP O: 각각초기화)
    printf("---Output A---\n");  
    printf("%d  %d  %d\n", A++, A++, A++);          // X방식(TEMP O: 각각초기화)
    // Window OS(L ← R):  X방식(TEMP O: 각각초기화)
    // TEMP A2 ← A1 ← A0: 7 ← 6 ← 5 각각 초기화/출력
    // Mac OS(L → R):     X방식(TEMP O: 각각초기화)
    // 5 → 6 → 7

    int B;                                          // 예: 5 입력/저장
    printf("---input B---\n");   
    scanf("%d", &B);                                // X방식(TEMP O: 각각초기화)
    printf("---Output B---\n");  
    printf("%d  %d  %d\n", ++B, ++B, ++B);          // X방식(TEMP O: 각각초기화) ← 本 Y 방식(TEMP 작동 X)
    // Window OS(L ← R):  X방식(TEMP O: 각각초기화)
    // TEMP B2 ← B1 ← B0: 8 ← 7 ← 6 각각 초기화/출력
    // Mac OS(L → R):     X방식(TEMP O: 각각초기화)
    // 6 → 7 → 8

    int C;  
    printf("---input C---\n");                      // 예: 7 입력/저장
    scanf("%d", &C);                                // X방식(TEMP O: 각각초기화)
    printf("---Output C---\n");  
    printf("%d  %d  %d  %d\n", C++, ++C, C++, ++C); // 후위연산자: X방식(TEMP O: 각각초기화) + 전위연사자: X방식(TEMP O: 각각초기화) ← 本 Y 방식(TEMP 작동 X)
    // Window OS(L ← R):  후위연산자: X방식(TEMP O: 각각초기화) + 전위연사자: X방식(TEMP O: 각각초기화)
    // 1) ++C(TEMP X): ++ (8 상태) → C =  8 초기화/출력   2) C++(TEMP O): C =  8 초기화상태 유지/출력 → ++( 9 상태)
    // 3) ++C(TEMP X): ++(10 상태) → C = 10 초기화/출력   4) C++(TEMP O): C = 10 초기화상태 유지/출력 → ++(11 상태)
    // ∴  10  10  8  8
    // Mac OS(L → R):
    // 7 → 9 → 9 → 11

    int D;                                                                  // 예: 8 입력/저장
    int E;                                                                  // 예: 9 입력/저장
    printf("---input C & D---\n");                                            
    scanf("%d", &D);                                                        // X방식(TEMP O: 각각초기화)
    scanf("%d", &E);                                                        // X방식(TEMP O: 각각초기화)
    printf("---Output C & D---\n");  
    printf("%d  %d  %d  %d  %d\n", D += E, D -= E, D *= E, D /= E, D %= E); // X방식(TEMP O: 각각초기화)
    // Window OS(L ← R):  X방식(TEMP O: 각각초기화)
    // TEMP D4 ← D3 ← D2 ← D1 ← TEMP D[0]0: 0 ← -9 ← 0 ← 0 ← 8 초기화/출력
    // Mac OS(L → R):     X방식(TEMP O: 각각초기화)
    // 17 → 8 → 72 → 8 → 8

    return 0;
}


```

`Window OS`
![](https://t9003081320.p.clickup-attachments.com/t9003081320/1c656201-4d48-4dee-b0c7-e82cffaef272/Picture2.png)

**opt\_aa\_12.c**

```plain
#include <stdio.h>
// 증감연산 한줄 출력 X:  이유 1: OS 차이 → 출력 차이,   이유 2: 가시성 ↓
// scanf 사용 O: 배열
int main()
{
    int A[3] = {3, 5, 8};                                    // X방식(TEMP O: 각각초기화)
    printf("---input A---\n");  
    for (int i = 0; i < 3; i++)
    {
        scanf("%d", &A[i]);                                  // 예: i = 0 일때 3, i = 1 일때 5, i = 2 일때 8 입력/저장 
    }
    // printf("---Output A---\n");  
    // printf("%d  %d  %d\n", A[1]++, A[1]++, A[1]++);       // X방식(TEMP O: 각각초기화)
    // Window OS(L ← R):  X방식(TEMP O: 각각초기화)
    // TEMP A[1]2 ← A[1]1 ← A[1]0: 7 ← 6 ← 5 각각 초기화/출력
    // Mac OS(L → R):     X방식(TEMP O: 각각초기화)
    // 5 → 6 → 7

    int B[3];                                                // X방식(TEMP O: 각각초기화)
    printf("---input B---\n");  
    for (int i = 0; i < 3; i++)
    {
        scanf("%d", &B[i]);                                  // 예: i = 0 일때 3, i = 1 일때 5, i = 2 일때 8 입력/저장 
    }
    printf("---Output B---\n");  
    printf("%d  %d  %d\n", ++B[1], ++B[1], ++B[1]);          // X방식(TEMP O: 각각초기화) ← 本 Y 방식(TEMP 작동 X)
    // Window OS(L ← R):  X방식(TEMP O: 각각초기화)
    // TEMP B[1]2 ← B[1]1 ← B[1]0: 8 ← 7 ← 6 각각 초기화/출력
    // Mac OS(L → R):     X방식(TEMP O: 각각초기화)
    // 6 → 7 → 8

    int C[3];                                                   // X방식(TEMP O: 각각초기화)
    printf("---input C---\n");  
    for (int i = 0; i < 3; i++)
    {
        scanf("%d", &C[i]);                                     // 예: i = 0 일때 3, i = 1 일때 7, i = 2 일때 8 입력/저장 
    }
    printf("---Output C---\n");
    printf("%d  %d  %d  %d\n", C[1]++, ++C[1], C[1]++, ++C[1]); // 후위연산자: X방식(TEMP O: 각각초기화) + 전위연사자: X방식(TEMP O: 각각초기화) ← 本 Y 방식(TEMP 작동 X)
    // Window OS(L ← R):  후위연산자: X방식(TEMP O: 각각초기화) + 전위연사자: X방식(TEMP O: 각각초기화)
    // 1) ++C(TEMP X): ++ (8 상태) → C =  8 초기화/출력   2) C++(TEMP O): C =  8 초기화상태 유지/출력 → ++( 9 상태)
    // 3) ++C(TEMP X): ++(10 상태) → C = 10 초기화/출력   4) C++(TEMP O): C = 10 초기화상태 유지/출력 → ++(11 상태)
    // ∴  10  10  8  8
    // Mac OS(L → R):
    // 7 → 9 → 9 → 11

    int D[3];                                                                                             // X방식(TEMP O: 각각초기화)
    int E[3];                                                                                             // X방식(TEMP O: 각각초기화)
    printf("---input C & D---\n");  
    for (int i = 0; i < 3; i++)
    {
        scanf("%d", &D[i]);                                                                               // 예: i = 0 일때 3, i = 1 일때 8, i = 2 일때 12 입력/저장
    }
    for (int i = 0; i < 3; i++)
    {
        scanf("%d", &E[i]);                                                                               // 예: i = 0 일때 2, i = 1 일때 4, i = 2 일때  9 입력/저장
    }
    // for (int i = 0; i < 3; i++)
    // {
    //     scanf("%d", &D[i]);                                                                            // 예: i = 0 일때 3, i = 1 일때 8, i = 2 일때 12 입력/저장
    //     scanf("%d", &E[i]);                                                                            // 예: i = 0 일때 2, i = 1 일때 4, i = 2 일때  9 입력/저장
    //                                                                                                    //  → D[0] = 3, E[0] = 8 / D[1] = 12, E[0] = 2 / D[2] = 4, E[2] = 9  
    // }
    printf("---input D---\n");  
    printf("---Output C & D---\n");
    printf("%d  %d  %d  %d  %d\n", D[1] += E[2], D[1] -= E[2], D[1] *= E[2], D[1] /= E[2], D[1] %= E[2]); // X방식(TEMP O: 각각초기화)
    // Window OS(L ← R):  X방식(TEMP O: 각각초기화)
    // TEMP D[0]4 ← D[0]3 ← D[0]2 ← D[0]1 ← D[0]0: 0 ← -9 ← 0 ← 0 ← 8 초기화/출력
    // Mac OS(L → R):     X방식(TEMP O: 각각초기화)
    // 17 → 8 → 72 → 8 → 8

    return 0;
}


```