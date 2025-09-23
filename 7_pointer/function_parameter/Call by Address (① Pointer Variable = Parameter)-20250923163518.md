# Call by Address (① Pointer Variable = Parameter)

## **Call by Address**
## **→ Parameter = Pointer Variable**
사용자정의 함수 (매개변수 = 포인터변수)

### **Significance 의의**

Premise Condition
❶ 사용자정의 함수 사용
❷ 사용자정의 함수 종료후에도 외부에 정의된 함수의 변수값 초기화/변경할 경우
※ 사용자정의 함수 사용 이유
*   Simplify Main Function Code 메인 함수 코드 간소화
*   Useful for Code Modification & Extension 코드 수정 및 확장 용이

1) 외부에 정의된 함수(메인 함수 포함)의 "2개 이상의 변수값"을 초기화/변경할 경우
외부에 정의된 함수(메인 함수 포함)의 "2개 이상의 변수값"을 "1개"의 사용자정의 함수에서 "한번에" 초기화/변경 要
\= 사용자정의 함수의 2개 이상의 변수값 "Return 반환" 이라고함
→ 사용자정의 함수의 2개 이상의 변수값 "Return 반환"하지않는데 용어 사용 이유

매개변수 Parameter를 2개 이상의 변수값을 사용하는데 용어 사용 이유

∵ "Return 반환"
ⓐ 원래(本) 사용자정의 함수의 "Return 반환"의 의미

\= 사용자정의 함수 실행 "결과값"을 외부에 정의된 함수의 변수값 초기화/변경

ⓑ 사용자정의 함수의 2개 이상의 변수값 "Return 반환" 의미
≠ 원래(本) 사용자정의 함수의 "Return 반환"의 의미
\= 사용자정의 함수 실행으로 "인해" 외부에 정의된 함수의 변수값 초기화/변경
i.e.) ⓐⓑ의 역할(외부에 정의된 함수의 변수값 초기화/변경)이 동일
∴ "Return 반환" 용어 사용

2) 배열을 매개변수 Parameter로 사용할 경우
배열은 매개변수 Parameter로 사용되지 않음
∵ 배열은 포인터변수로 붕괴됨
e.g.) X ➝(붕괴 O)➝ &X\[0\]
∴ 배열을 매개변수 Parameter로 사용하면 포인터변수로 사용됨
∴ 배열을 매개변수 Parameter로 사용하려면 인수를 포인터변수로 사용해야함

* * *
* * *

## **1) (n) of External Variables ≥ 2 외부 변수 갯수 ≥ 2**

#### **1)A (n) of External Variables = 1 외부 변수 갯수 = 1**
➝ 외부에 정의된 함수의 "1개 변수값"을 초기화/변경할 경우

**func\_parameter\_1.c**
메인 함수 변수값 10 증가 ➝ 포인터변수 사용

```cpp
#include <stdio.h>

void add_10(int *variable)
{
    *variable = *variable + 10;
}

int main()
{
    int X = 0;
    int *X_ptr = &X;

    add_10(&X);              
    printf("X: %d\n", X);
    
    add_10(X_ptr);           
    printf("X: %d\n", X);

    return 0;
}


```

① 함수 사용 이유
*   Useful for Code Modification & Extension 코드 수정 및 확장 용이

E.g.)

여기서 사용자정의 함수 `add_10` 호출이 메인 함수에서 1개 뿐이지만

메인 함수 + 사용자정의 함수 `add_10` + 다른 사용자정의 함수내

`add_10` + 다른 파일의 메인 함수/사용자정의 함수내 `add_10`이 존재할 때

사용자정의 함수 코드 변경(e.g. + 10 ➝ - 10) 하려면

사용자정의 함수 `add_10` 수정만 필요

※ Global Variable 전역 변수는 함수를 사용하여 변경하기보다 직접 변경 용이

② 포인터변수 사용 이유
➝ 메인 함수에서 직접 변수값 변경하면 되는데
굳이 사용자정의 함수까지 사용하면서 포인터변수 사용 이유
*   없음

**func\_parameter\_2.c**
메인 함수 변수값 10 증가 ➝ Return 반환 사용

```cpp
#include <stdio.h>

int add_10(int variable)
{
    return variable + 10;
}

int main()
{
    int X = 0;

    X = add_10(X);           
    printf("X: %d\n", X);
    
    return 0;
}


```

i.e.) 외부에 정의된 함수의 "1개 변수값"을 초기화/변경할 경우
➝ 포인터변수로 접근 하지 않아도, Return 사용으로 보다 용이하게 가능

#### **1)B (n) of External Variables** ≥ **2 외부 함수 변수 갯수** ≥ **2**
➝ 외부에 정의된 함수의 "2개 이상의 변수값"을 초기화/변경할 경우

**func\_parameter\_3.c**
메인 함수 2개 변수값 Swap

```perl
#include <stdio.h>

void swap_int(int variable_1, int variable_2)
{
    int variable_temp;
    variable_temp = variable_1;
    variable_1 = variable_2;
    variable_2 = variable_temp;

    printf("swap_int\nvariable_1: %d, variable_2: %d\n", variable_1, variable_2);
}

void swap_ptr(int *variable_1, int *variable_2)
{
    int variable_temp;
    variable_temp = *variable_1;
    *variable_1 = *variable_2;
    *variable_2 = variable_temp;

    printf("swap_ptr\nvariable_1: %d, variable_2: %d\n", *variable_1, *variable_2);
}

int main()
{
    int X;
    int Y;

    printf("정수 1 :");
    scanf("%d", &X);
    printf("정수 2 :");
    scanf("%d", &Y);

    swap_int(X, Y);
    printf("X: %d Y: %d\n", X, Y);

    swap_ptr(&X, &Y);
    printf("X: %d Y: %d\n", X, Y);

    return 0;
}


```

① 함수 사용 이유
*   Simplify Main Function Code 메인 함수 코드 간소화
*   Useful for Code Modification & Extension 코드 수정 및 확장 용이

E.g.)

여기서 사용자정의 함수 `swap_ptr` 호출이 메인 함수에서 1개 뿐이지만

메인 함수 + 사용자정의 함수 `swap_ptr` + 다른 사용자정의 함수내

`swap_ptr` + 다른 파일의 메인 함수/사용자정의 함수내 `swap_ptr`이 존재할 때

사용자정의 함수 코드 변경(e.g. \*variable\_1 = \*variable\_1 + 10) 하려면

사용자정의 함수 `swap_ptr` 수정만 필요

② 포인터변수 사용 이유
➝ 메인 함수에서 직접 변수값 변경하면 되는데
굳이 사용자정의 함수까지 사용하면서 포인터변수 사용 이유

Premise Condition

★ 上 사용자정의 함수 사용 이유로 인해, 사용자정의 함수를 사용해야함

★ 사용자정의 함수 종료후에도 외부에 정의된 함수의 변수값 초기화/변경할 경우

*   외부에 정의된 함수의 "2개 이상의 변수값"을 초기화/변경할 경우
∵ 사용자정의 함수의 "Return 갯수는 1개" ➝ Return 사용 X
e.g.) int function ( ){ } ➝ int 값 Return, void function ( ){ } ➝ Return 無
∴ "2개 이상의 변수값"을 초기화/변경할 경우 포인터변수를 사용할수 밖에 없음
Ref) 대부분 Void 사용자정의 함수 사용 ➝ Return 사용 필요 X
때때로 Bool 사용자정의 함수 사용하여 함수 실행 동작 여부 Check 함
하지만 Code 작성 의도에 따라 int, float, char ... 사용자정의 함수 사용하기도 함

**func\_parameter\_4.c**
Score 10번 입력 ➝ 1ST ~ 3RD Place 출력
*   Argument 인수

\= 포인터변수

*   매개변수 Parameter

\= Argument 인수 = 포인터변수 ➝(초기화)

➝ "2개 이상의 변수값"(1ST ~ 3RD Place) 수정

```plain

#include <stdio.h>

void function_score (int *first_score, int *second_score, int *third_score, int score)
{
    if (score >= *first_score)
    {
        *third_score = *second_score;
        *second_score = *first_score;
        *first_score = score;
    }
    else if (score >= *second_score)
    {
        *third_score = *second_score;
        *second_score = score;
    }
    else if (score >= *third_score)
    {
        *third_score = score;
    }
}

int main()
{
    int first = 0;
    int second = 0;
    int third = 0;
    int input_score;

    int *first_ptr = &first;
    int *second_ptr = &second;
    int *third_ptr = &third;

    // 인수 = 포인터변수
    for (int i = 0; i < 10; i++)
    {
        printf("0 ~ 100 범위의 점수를 입력하세요:");
        scanf("%d", &input_score);
        if (0 <= input_score && input_score <= 100)
        {
            function_score (first_ptr, second_ptr, third_ptr, input_score);
        }
        else
        {
            printf("잘못된 점수를 입력하셨습니다. 다시 0 ~ 100 범위의 점수를 입력하세요:");
            i--;
        }
        
    }
    // // 인수 = 주소값
    // for (int i = 0; i < 10; i++)
    // {
    //     printf("0 ~ 100 범위의 점수를 입력하세요:");
    //     scanf("%d", &input_score);
    //     if (0 <= input_score && input_score <= 100)
    //     {
    //         function_score (&first, &second, &third, input_score);
    //     }
    //     else
    //     {
    //         printf("잘못된 점수를 입력하셨습니다. 다시 0 ~ 100 범위의 점수를 입력하세요:");
    //         i--;
    //     }
        
    // }

    printf("1등: %d\n", first);
    printf("2등: %d\n", second);
    printf("3등: %d\n", third);

    return 0;
}


```

① 함수 사용 이유
*   Simplify Main Function Code 메인 함수 코드 간소화
*   Useful for Code Modification & Extension 코드 수정 및 확장 용이

E.g.)

여기서 사용자정의 함수 `function_score` 호출이 메인 함수에서 1개 뿐이지만

메인 함수 + 사용자정의 함수 `function_score` + 다른 사용자정의 함수내

`function_score` + 다른 파일의 메인 함수/사용자정의 함수내 `swap_ptr`이 존재할

때 사용자정의 함수 코드 변경(e.g. first\_score += 10) 하려면

사용자정의 함수 `function_score` 수정만 필요

② 포인터변수 사용 이유
➝ 메인 함수에서 직접 변수값 변경하면 되는데
굳이 사용자정의 함수까지 사용하면서 포인터변수 사용 이유

Premise Condition

★ 上 사용자정의 함수 사용 이유로 인해, 사용자정의 함수를 사용해야함

★ 사용자정의 함수 종료후에도 외부에 정의된 함수의 변수값 초기화/변경할 경우

*   외부에 정의된 함수의 "2개 이상의 변수값"을 초기화/변경할 경우
∵ 사용자정의 함수의 "Return 갯수는 1개" ➝ Return 사용 X
e.g.) int function ( ){ } ➝ int 값 Return, void function ( ){ } ➝ Return 無
∴ "2개 이상의 변수값"을 초기화/변경할 경우 포인터변수를 사용할수 밖에 없음
Ref) 대부분 Void 사용자정의 함수 사용 ➝ Return 사용 필요 X
때때로 Bool 사용자정의 함수 사용하여 함수 실행 동작 여부 Check 함
하지만 Code 작성 의도에 따라 int, float, char ... 사용자정의 함수 사용하기도 함

* * *

## **2) Array = Parameter 배열 = 매개변수**

배열은 매개변수 Parameter로 사용되지 않음
∵ 배열은 포인터변수로 붕괴됨
e.g.) X ➝(붕괴 O)➝ &X\[0\]
∴ 배열을 매개변수 Parameter로 사용하면 포인터변수로 사용됨
∴ 배열을 매개변수 Parameter로 사용하려면 인수를 포인터변수로 사용해야함

```plain
void function_1(int array[])   // 매개변수로 배열을 사용 ➝ 포인터변수로 붕괴
                               // int &array[0][]
{
}

void function_2(int* array)    // 매개변수로 포인터 변수를 사용
{
}


```

※ function\_1 = function\_ 2

Ref)
**func\_parameter\_5.c**

```perl
// Case #1
#include <stdio.h>

int add_10 (int number[])
{
    return number[1] + 10;
}

int main()
{
    int X[3] = {1, 2, 3,};

    X[1] = add_10(X);
   
    printf("X: %d\n", X[1]);
    
    return 0;
}

// Case #2
#include <stdio.h>

int add_10(int number[], int place)
{
    return number[place] + 10;
}

int main()
{
    int X[3] = {1, 2, 3};

    int index = 0;

    int i = 0;
    while (1)
    {
        printf("0 ~ 2 범위의 배열 위치를 입력하세요: ");
        scanf("%d", &index);
        if (0 <= index && index <= 2)
        {
            break;
        }
        else
        {
            printf("잘못된 범위의 배열 위치를 입력하셨습니다.");
        }
    }

    X[index] = add_10(X, index);

    printf("X: %d\n", X[index]);

    return 0;
}


```

#### **※ 문자열 함수**

| 문자열 함수 | 요소<br>변경 | 요소<br>초기화 | 출력 |
| ---| ---| ---| --- |
| 함수(stirng\_1);<br>함수(string\_1, string\_2); | 배열 자체<br>printf(%s, string\_1); | 함수 반환값(Return)<br>printf("% ", 함수(string\_1));<br>printf("% ", 함수(string\_1, string\_2)); |
| strlen | X | X | 문자열(%s) | 반환값 → 문자열 길이(%d) |
| strcmp | X | X | 문자열(%s) | 반환값 → 0, -1, 1(%d) |
| strcat, strncat | O string\_1 | O string\_1 | 변경 문자열(%s) | 반환값 → 주소값(%p, %d) |
| strcpy, strncpy | O string\_1 | O string\_1 | 변경 문자열(%s) | 반환값 → 복사된 문자열에 대한 포인터(%p, %d) |
|  |  |  |  | 위의 함수들의 반환값은 문자열 변경 X<br>∴ 반환값을 초기화할 필요 X<br>∴ 배열 출력 필요 O |
| toupper, tolower | O string\_1 | X | 변수에 초기화시<br>변경 문자열(%s) | 반환값 → 문자 1개(%c)<br><br>변경 문자열(%s)<br>∴ 출력값 無 (Segmentation Fault)<br>∴ 전체 초기화 필요 O<br>초기화 하지 않아도<br>변경문자 1개 출력가능 O(%c)<br>변경문자 1개 ASCII Code 변환정수 출력가능 O(%d) |

![](https://t9003081320.p.clickup-attachments.com/t9003081320/3f2c50ec-e48b-4361-b18d-1aab336aac41/Picture2.jpg)

#### **2)A strncat & strcat**
➝ 문자열 연결
*   `strncat(X, Y, n);` // Y문자열 n개를 X문자열의 Null('\\0') 부터 연결후 Null('\\0') 생성
*   `strcat(X, Y);` // Y문자열을 X문자열의 Null('\\0') 부터 연결후 Null('\\0') 생성

`strncat(X, Y, n);`
**func\_parameter\_6.c**
ⓐ 함수사용

```cpp
#include <stdio.h>
#include <string.h>

int main()
{
    char X[10];
    char Y[20];

    printf("문자열 1: ");
    scanf("%s", X);
    printf("문자열 2: ");
    scanf("%s", Y);

    printf("%s\n", X);
    printf("%s\n", Y);

    strncat(X, Y, 3);        //  Y문자열을 X문자열의 null 부터 3개 연결후 Null('\0')생성
    printf("%s\n", X);

    return 0;
}
          
```

**func\_parameter\_7.c**
ⓑ 직접구현

```cpp
#include <stdio.h>

void manual_strncat(char *char_ptr1, char *char_ptr2, int text_number)
{
    char *null_address = char_ptr1;
    while (*null_address != 0)             // *null_address ! = Null('\0')
    {
        null_address += 1;                 // &X[0] ➝ &X[1] ➝ &X[2] ...   결국, null_address = X 문자열의 Null('\0') 주소값
    }

    for (int i = 0; i < text_number; i++)
    {
        *(null_address + i) = *(char_ptr2 + i);
    }
    *(null_address + text_number) = 0;     // Null('\0') 생성
}

int main()
{
    char X[10];
    char Y[20];

    printf("문자열 1: ");
    scanf("%s", X);
    printf("문자열 2: ");
    scanf("%s", Y);

    printf("%s\n", X);
    printf("%s\n", Y);

    manual_strncat(X, Y, 3);    // manual_strncat(&X[0], &Y[0], 3); 

    printf("==========\n");
    printf("%s", X);

    return 0;
}


```

`strcat(X, Y);`
**func\_parameter\_8.c**
ⓐ 함수사용

**func\_parameter\_9.c**
ⓑ 직접구현

#### **2)B strncpy & strcpy**
➝ 문자열 복사

`strncpy(X, Y, n);`
*   Y 문자열을 X 문자열 0번째 자리부터 복사
*   복사 이후 마지막 문자열에 Null('\\0') 추가 X
∴ scanf %s 정상 출력을 위한 방법 1: 마지막 문자에 Null('\\0') 수동 입력
∴ scanf %s 정상 출력을 위한 방법 2: 문자열 초기화를 위한 배열 선언시 Null('\\0') Set-up
E.g) char X\[5\] = {0};
`strcpy(X, Y);`
*   Y 문자열 n개를 X 문자열 0번째 자리부터 복사
*   복사 이후 마지막 문자열에 Null('\\0') 추가 O

*   `strncpy(X, Y, n);` // Y 문자열 n개를 X 문자열 0번째 자리부터 복사

//  복사 이후 마지막 문자열에 Null('\\0') 추가 X

※ X 문자열 Length > Y 문자열 복사할 Length

E.g.) X = ABCDEFG, Y = abcdefg, n = 3

abcDEFG

※ X 문자열 Length < Y 문자열 복사할 Length

E.g. #1) X 배열 전체 메모리박스 크기 < Y 문자열 복사할 Length

Overflow 발생

char X\[3\]; Y = abcdefg, n = 5

E.g. #2) X = ABC, Y = abcdefg, n = 5

abcde
➝ X 문자열 위치에서 e 다음 문자 위치에
쓰레기값 int 0 ➝(ASCII Code)➝ char '\\0' 있어
정상출력 됨

※ X 문자열 Length = Y 문자열 복사할 Length

E.g.) X = ABCDE, Y = abcde, n = 5

abcde

➝ X 문자열 위치에서, e 다음 문자 위치에

쓰레기값이 ( int 0 ➝(ASCII Code)➝ char '\\0') 이 있어

정상출력 됨

※ Y 문자열 Length < n

Y 문자열 나머지 문자열에 Null('\\0') 초기화 후 복사

E.g.) X= ABCDEFG, Y = abc, n = 5 // Y = abc\\0\\0

abc(\\0\\0FG)

∴ scanf %s 정상 출력을 위한 방법 1: 마지막 문자에 Null('\\0') 수동 입력

∴ scanf %s 정상 출력을 위한 방법 2: 문자열 초기화를 위한 배열 선언시 Null('\\0') Set-up

E.g) char X\[5\] = {0};

**⇒**  `strncpy(X, Y, n);` **사용하기 불안정한 함수 ➝ 사용 권장 X**

*   `strcpy(X, Y);` // Y 문자열을 X 문자열 0번째 자리부터 복사

//  복사 이후 마지막 문자열에 Null('\\0') 추가 O

※ X 문자열 Length > Y 문자열 Length

Y 문자열 복사후 Null('\\0') 추가 ?!?!?

Y 문자열 + Null('\\0')을 복사 ?!?!?

E.g.) X = ABCDEFG, Y = abc

abc(\\0EFG)

※ X 문자열 Length < Y 문자열 Length

E.g. #1) X 배열 전체 메모리박스 크기 < Y 문자열 Length

Overflow 발생

char X\[3\]; Y = abcde

E.g. #2) X = ABC, Y = abcdefg

abcdefg(\\0)

※ X 문자열 Length = Y 문자열 Length

E.g. #1) X 배열 전체 메모리박스 크기 = Y 문자열 Length

Overflow 발생 ➝ Null('\\0') 생성 공간 초과

char X\[5\]; char Y\[5\]; X\[6\] = Null('\\0')

E.g. #2) X = ABCDE, Y = abcde

abcde(\\0)

`strncpy(X, Y, 3);`
**func\_parameter\_10.c**
ⓐ 함수사용

```cpp
#include <stdio.h>
#include <string.h>

int main()
{
    char X[10] = {0};
    char Y[20] = {0};

    printf("문자열 1: ");
    scanf("%s", X);
    printf("문자열 2: ");
    scanf("%s", Y);

    printf("%s\n", X);
    printf("%s\n", Y);

    strncpy(X, Y, 3);         
    printf("%s\n", X);

    for (int i = 0; i < 10; i++)
    {
        printf("%c\n", X[i]);
    }

    return 0;
}


```

**func\_parameter\_11.c**
ⓑ 직접구현

```cpp
#include <stdio.h>

void manual_strncpy(char *char_ptr1, char *char_ptr2, int text_number)
{
    for (int i = 0; i < text_number; i++)
    {
        *(char_ptr1 + i) = *(char_ptr2 + i);
    }
}

int main()
{
    char X[10] = {0};
    char Y[20] = {0};

    printf("문자열 1: ");
    scanf("%s", X);
    printf("문자열 2: ");
    scanf("%s", Y);

    printf("%s\n", X);
    printf("%s\n", Y);

    manual_strncpy(X, Y, 3);   // manual_strncpy(&X[0], &Y[0], 3); 

    printf("=====\n");
    printf("%s", X);
    
    for (int i = 0; i < 10; i++)
    {
        printf("%c\n", X[i]);
    }

    return 0;
}


```

`strcpy(X, Y);`
**func\_parameter\_12.c**
ⓐ 함수사용

**func\_parameter\_13.c**
ⓑ 직접구현

#### **2)C strncmp & strcmp**
➝ 문자열 변경
*   `strncmp(X, Y, 3);` // X, Y 문자열 3개 비교
*   `strcmp(X, Y);` // X, Y 문자열 비교

`strncmp(X, Y, 3);`
**func\_parameter\_14.c**
ⓐ 함수사용

**func\_parameter\_15.c**
ⓑ 직접구현

`strcmp(X, Y);`
**func\_parameter\_16.c**
ⓐ 함수사용

**func\_parameter\_17.c**
ⓑ 직접구현

#### **2)D toupper & tolower**
➝ 대문자 & 소문자 변경
*   `toupper( );` // 소문자 ➝ 대문자 변경
*   `tolower( );` // 대문자 ➝ 소문자 변경

`toupper( );`
**func\_parameter\_18.c**
ⓐ 함수사용

**func\_parameter\_19.c**
ⓑ 직접구현

`tolower( );`
**func\_parameter\_20.c**
ⓐ 함수사용

**func\_parameter\_21.c**
ⓑ 직접구현