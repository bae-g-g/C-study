# Multi-Dimensional Array

## **Multi-Dimensional Array 다차원 배열**

이전차원의 배열을 어러개 가지는 배열
1차원 배열 = 데이터타입(≒ 0차원 배열) n 개
2차원 배열 = 1차원 배열(X축) n개(Y축)
3차원 배열 = 2차원 배열(X축\*Y축) n개(Z축)
예:
`int array [n3][n2][n1];`
n1 = X축 1차원 배열 크기
n2 = Y축 2차원 배열 크기
n3 = Z축 3차원 배열 크기

1차원 배열
`int array[4];`
![](https://t9003081320.p.clickup-attachments.com/t9003081320/8dd6064c-306f-49b8-9481-79dee790f439/Picture1.png)
0차원배열 4개 (4개: X축)

2차원 배열
`int array[2][4];`
![](https://t9003081320.p.clickup-attachments.com/t9003081320/a9225882-2985-461a-b24a-4c8f2553772a/Picture2.png)
배열 크기 4의 1차원 배열 2개 (2개: Y축, 4개: X축)

3차원 배열
`int array[2][2][4];`
![](https://t9003081320.p.clickup-attachments.com/t9003081320/0aa6b962-c6aa-45a6-9f9b-7f82c1c6c042/Picture4.png)
배열 크기 4 의 1차원 배열을 2개 가진 2차원 배열이 2개 (2개: Z축, 2개: Y축, 4개: X축)

### **Structure 구조**

**크기(Size)**
예:
`int array [n3][n2][n1];`
n1 = X축 1차원 배열 크기 = 0차원(자료형) 갯수
n2 = Y축 2차원 배열 크기 = 1차원 배열 갯수
n3 = Z축 3차원 배열 크기 = 2차원 배열 갯수

1차원 배열 크기 = n1
**d\_multi\_arr\_1\_a.c**

```perl
#include <stdio.h>

int main()
{
    int array[10];
    int total_bytes = sizeof(array);            // 총 Bytes
    int each_bytes = sizeof(array[0]);          // 메모리박스 1개 Byte
    int array_size = total_bytes / each_bytes;  // 총 Bytes / 메모리박스 1개 Byte = 배열 크기

    printf("%d\n", total_bytes);
    printf("%d\n", sizeof(array));
    printf("%d\n", each_bytes);
    printf("%d\n", sizeof(array[0]));
    printf("%d\n", array_size);

    // int X, Y, Z;
    // Z = X + Y;
    // printf("%d\n", Z);
    // printf("%d\n", X + Y);

    return 0;
}
```

다차원 배열 크기 = n1 x n2 x n3 .... nn
**d\_multi\_arr\_1\_b.c**

```cpp
#include <stdio.h>

int main()
{
    int array[3][2][10];
    int total_bytes = sizeof(array);             // 총 Bytes
    int each_bytes = sizeof(array[0][0][0]);     // 메모리박스 1개 Byte
    int array_size = total_bytes / each_bytes;   // 총 Bytes / 메모리박스 1개 Byte = 배열 크기

    printf("%d\n", total_bytes);
    printf("%d\n", each_bytes);
    printf("%d\n", array_size);
    return 0;
}
```

**색인(index)**
예:
`int array [n3][n2][n1];` 선언
`array [2][1][9] = 100;` 초기화 (1차원배열 9번째, 2차원배열 1번째, 3차원 배열 2번째 위치)

**d\_multi\_arr\_1\_c.c**

```cpp
// Approach 1
#include <stdio.h>

int main()
{
    int array[3][2][10] = {0};          // \0 = null Set-Up
    array[2][1][9] = 100;
    // int array[10];
    // array[3] = 100;

    printf("%d\n", array[2][1][9]);

    return 0;
}


// Approach 2
#include <stdio.h>

int main()
{
    int array[3][2][10] = {0};          // \0 = null Set-Up
    int X = 0;

    // 초기화
    for (int i = 0; i < 3; i++)              
    {
        for (int j = 0; j < 2; j++)          
        {
            for (int k = 0; k < 10; k++)     
            {
                // int X = 0;
                array[i][j][k] = X;         
                X++;                        
            }
        }
    }

    // 출력
    for (int i = 0; i < 3; i++)
    {
        for (int j = 0; j < 2; j++)
        {
            for (int k = 0; k < 10; k++)
            {
                printf("array[%d][%d][%d]: %d\n", i, j, k, array[i][j][k]);
            }
        }
    }

    return 0;
}
```

**요소(Element)**
색인(Index)에 초기화 값

### **Address 주소값**
1차원 배열의 0번째 색인(Index) 부터 요소/자료형 크기만큼 증가
예:
`int arr[2][4];`
주소값
`arr[0][0]` ➝ `arr[0][1]` ➝ .... ➝ `arr[0][3]` ➝ `arr[1][0]` ➝ `arr[1][1]` ➝ ... ➝ `arr[1][3]` 4씩 증가

**d\_multi\_arr\_1\_d.c**

```perl
#include <stdio.h>

int main()
{
    int array[2][4] = {0};            // \0 = null Set-Up

    printf("요소 출력\n");  
    for (int i = 0; i < 2; i++)
    {
        for (int j = 0; j < 4; j++)
        {
            printf("array[%d][%d] 요소: %d\n", i, j, array[i][j]);
        }
    }
    printf("주소 출력\n");  
    for (int i = 0; i < 2; i++)
    {
        for (int j = 0; j < 4; j++)
        {
            printf("array[%d][%d] 주소: %d\n", i, j, &array[i][j]);
        }
    }

    return 0;
}
```

### **Example)**

**d\_multi\_arr\_2.c**

```prolog
#include <stdio.h>

int main()
{
    // 2차원 배열:  배열크기 4의 1차원 배열 2개
    int array_1[2][4] = {{0, 1, 2, 3}, {4, 5, 6, 7}};  
    int array_2[2][4];                                
    int array_3[2][4];                               
 
    // 선언 후 초기화 1: 직접 초기화 array_2
    array_2[0][0] = 0;
    array_2[0][1] = 1;
    array_2[0][2] = 2;
    array_2[0][3] = 3;
    array_2[1][0] = 4;
    array_2[1][1] = 5;
    array_2[1][2] = 6;
    array_2[1][3] = 7;

    // 선언 후 초기화 2: 반복문으로 초기화 array_3
    for (int i = 0; i < 2; i++)
    {
        for (int j = 0; j < 4; j++)
        {
            array_3[i][j] = i * 4 + j;
        }
    }

    // 출력 1: 직접 요소 출력 array_1
    printf("array_1: %d\n", array_1[0][0]);
    printf("array_1: %d\n", array_1[0][1]);
    printf("array_1: %d\n", array_1[0][2]);
    printf("array_1: %d\n", array_1[0][3]);
    printf("array_1: %d\n", array_1[1][0]);
    printf("array_1: %d\n", array_1[1][1]);
    printf("array_1: %d\n", array_1[1][2]);
    printf("array_1: %d\n", array_1[1][3]);
    printf("====================\n");

    // 출력 2: 직접 요소 출력 array_2
    printf("array_2: %d\n", array_2[0][0]);
    printf("array_2: %d\n", array_2[0][1]);
    printf("array_2: %d\n", array_2[0][2]);
    printf("array_2: %d\n", array_2[0][3]);
    printf("array_2: %d\n", array_2[1][0]);
    printf("array_2: %d\n", array_2[1][1]);
    printf("array_2: %d\n", array_2[1][2]);
    printf("array_2: %d\n", array_2[1][3]);
    printf("====================\n");

    // 출력 3-1: 반복문 요소 출력 array_3
    for (int i = 0; i < 2; i++)
    {
        for (int j = 0; j < 4; j++)
        {
            printf("array_3[%d][%d]요소: %d\n", i, j, array_3[i][j]);
        }
    }
    // 출력 3-2: 반복문 주소 출력
    for (int i = 0; i < 2; i++)
    {
        for (int j = 0; j < 4; j++)
        {
            printf("array_3[%d][%d]주소: %d\n", i, j, &array_3[i][j]);
        }
    }

    return 0;
}
```

**d\_multi\_arr\_3.c**

```cpp
#include <stdio.h>

int main()
{
    int array_int[2][4];       // X축 4개 Y축 2개 = 8개  x  4 Bytes  =  32 Bytes
    char array_char[2][4];     // X축 4개 Y축 2개 = 8개  x  1 Bytes  =   8 Bytes
    float array_float[2][4];   // X축 4개 Y축 2개 = 8개  x  4 Bytes  =  32 Bytes

    printf("  int array size: %d\n", sizeof(array_int));
    printf(" char array size: %d\n", sizeof(array_char));
    printf("float array size: %d\n", sizeof(array_float));

    return 0;
}
```

**d\_multi\_arr\_4.c**

```perl
#include <stdio.h>

int main()
{
    int array[3][2][4];

    printf("=============크기 출력=============\n");
    printf("int array[3][2][4] 크기:\n(3*2*4)*4 = %d\n", sizeof(array));

    printf("===============초기화==============\n");
    int element = 0;
    for (int i = 0; i < 3; i++)
    {
        for (int j = 0; j < 2; j++)
        {
            for (int k = 0; k < 4; k++)
            {
                // int element = 0;
                array[i][j][k] = element;  // 작성 X  →  초기화 X
                printf("int array[%d][%d][%d] %d 초기화\n", i, j, k, element);  
                printf("int array[%d][%d][%d] %d 초기화\n", i, j, k, array[i][j][k]); 
                element++;
            }
        }
    }

    printf("==============요소 출력==============\n");
    for (int i = 0; i < 3; i++)
    {
        for (int j = 0; j < 2; j++)
        {
            for (int k = 0; k < 4; k++)
            {
                printf("int array 요소[%d][%d][%d]: %d 출력\n", i, j, k, array[i][j][k]);
            }
        }
    }

    printf("==============주소 출력==============\n");
    printf("int array 주소: %d\n", &array);
    for (int i = 0; i < 3; i++)
    {
        for (int j = 0; j < 2; j++)
        {
            for (int k = 0; k < 4; k++)
            {
                printf("int array 주소[%d][%d][%d]: %d 출력\n", i, j, k, &array[i][j][k]);
            }
        }
    }    

    return 0;
}
```

**d\_multi\_arr\_5.c**

```
#include <stdio.h>

// 2차원배열 선언 동시 초기화
int main()
{
    char array[5][12] = {"array[0]", "array[1]", "array[2]", "array[3]", "array[4]"};   
    //  array[0][n] = "array[0]" (array[0] → 1차원배열 각 요소 a r r a y [ 0 ]),   array[1][n] = "array[1]" (array[1] → 1차원배열 각 요소 a r r a y [ 1 ]) .......
    
    // 2차원배열 각 색인(Index) 마다 문자열(1차원배열 각 요소) 확인
    printf("array[n][n]\n");
    for (int i = 0; i < 5; i++)
    {
        printf("array[%d]   : %s\n", i, array[i]);
    }

    // 2차원배열 각 색인(Index) 마다 문자 1개씩 확인
    printf("\narray[0][n]\n");
    for (int i = 0; i < 12; i++)
    {
        printf("array[0][%d]: %c\n", i, array[0][i]);  //  array[0][8] 부터 \0 = null 초기화   ∵ "array[0]" 문자열상수 → 문자열상수 마지막 \0 = null 문자 자동 생성/인식 O
    }
    printf("\narray[1][n]\n");
    for (int i = 0; i < 12; i++)
    {
        printf("array[1][%d]: %c\n", i, array[1][i]);
    }
    printf("\narray[2][n]\n");
    for (int i = 0; i < 12; i++)
    {
        printf("array[2][%d]: %c\n", i, array[2][i]);
    }
    printf("\narray[3][n]\n");
    for (int i = 0; i < 12; i++)
    {
        printf("array[3][%d]: %c\n", i, array[3][i]);
    }
    printf("\narray[4][n]\n");
    for (int i = 0; i < 12; i++)
    {
        printf("array[4][%d]: %c\n", i, array[4][i]);
    }
    
    printf("==============\n");
    for (int i = 0; i < 5; i++)
    {
        printf("\narray[%d][n]\n", i);
        for (int j = 0; j < 12; j++)
        {
            printf("array[%d][%d]: %c\n", i, j, array[i][j]);
            
        }
    }

    return 0;
}

// 2차원 배열 선언 후 초기화
#include <stdio.h>

int main()
{   
    char array[5][12] = {0}; 

    for (int i = 0; i < 5; i++)
    {
        scanf("%s", &array[i]);
    }

    printf("\narray[n][n]\n");
    for (int i = 0; i < 5; i++)
    {
        printf("array[%d]   : %s\n", i, array[i]);
    }

    // 문자 1개씩 확인
    printf("\narray[0][n]\n");
    for (int i = 0; i < 12; i++)
    {
        printf("array[0][%d]: %c\n", i, array[0][i]);  //  array[0][8] 부터 \0 = null 초기화   ∵ "array[0]" 문자열상수 → 문자열상수 마지막 \0 = null 문자 자동 생성/인식 O
    }
    printf("\narray[1][n]\n");
    for (int i = 0; i < 12; i++)
    {
        printf("array[1][%d]: %c\n", i, array[1][i]);
    }
    printf("\narray[2][n]\n");
    for (int i = 0; i < 12; i++)
    {
        printf("array[2][%d]: %c\n", i, array[2][i]);
    }
    printf("\narray[3][n]\n");
    for (int i = 0; i < 12; i++)
    {
        printf("array[3][%d]: %c\n", i, array[3][i]);
    }
    printf("\narray[4][n]\n");
    for (int i = 0; i < 12; i++)
    {
        printf("array[3][%d]: %c\n", i, array[4][i]);
    }

    printf("==============\n");
    for (int i = 0; i < 5; i++)
    {
        printf("\narray[%d][n]\n", i);
        for (int j = 0; j < 12; j++)
        {
            printf("array[%d][%d]: %c\n", i, j, array[i][j]);
            
        }
    }

    return 0;
}
```

**d\_multi\_arr\_6.c** (← **e\_for\_while\_2.c**)
예:
구구단 출력 프로그램

```cpp
// 구구단 출력 프로그램

// Case 1-1: for 
#include <stdio.h>
int main()
{
    int array[10][10] = {0};
    for (int i = 2; i < 10; i++)                        // i = 몇단
    {
        for (int j = 1; j < 10; j++)                    // j = x 1 ~ 9
        {
            array[i][j] = i * j;
            printf("array[%d][%d]: %2d| ", i, j, array[i][j]);   
        }
        printf("\n");
    }
}

// Case 1-2: for
int main()
{   
    int array[10][10] = {0};
    for (int i = 1; i < 10; i++)                         // i = x 1 ~ 9
    { 
        for (int j = 2; j < 10; j++)                     // j = 몇단
        {
            array[j][i] = j * i;
            printf("array[%d][%d]: %2d| ", j, i, array[j][i]);   
        }
        printf("\n");
    }
}


// Case 2-1: while
int main()
{
    int array[10][10] = {0};
    int i = 2;
    int j = 1; 

    while (i < 10)            // i = 몇단
    {
        while (j < 10)        // j = x 1 ~ 9
        {
            array[i][j] = i * j;
            printf("array[%d][%d]: %2d| ", i, j, array[i][j]); 
            j++;
        }
        printf("\n");

        i++;
        j = 1;                // for문 처럼 j = 1(x 1 ~ 9) 초기화식 필요
    }
}

// Case 2-2: while
int main()
{
    int array[10][10] = {0};
    int i = 1;
    int j = 2;  

    while (i < 10)            // i = x 1 ~ 9
    {
        while (j < 10)        // j = 몇단
        {
            array[j][i] = j * i;
            printf("array[%d][%d]: %2d| ", j, i, array[j][i]);  
            j++;
        }
        printf("\n");

        i++;
        j = 2;                // for문 처럼 j = 2(몇단) 초기화식 필요
    }
}
```