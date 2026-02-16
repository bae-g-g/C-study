# ②ⓑ Return = Dynamic Memory

## **② Return Dynamic Memory Allocation 동적 메모리 반환**

Return (Dynamic Memory Allocation ➝ 포인터변수)

Dynamic Memory Allocation 동적 메모리 할당
*   HEAP Sector "할당" (느슨한 PRIORTY QUEUE 방식) = Run Time 시 할당
Ref) 동적 메모리 할당 함수 내부적으로 느슨한 PRIORTY QUEUE 방식 구현되어 있음
*   Life Cycle Memory 할당된 Code Block 시작 ~ Programme 종료 (Run Time 중 계속 유지)
*   사용자가 직접 할당하는 함수(malloc, calloc, relloc)의 Return (반환)
*   사용자가 직접 할당하는 동적 메모리 할당은 Computer Programme과 Service에 Physical 물리적/Virtual 가상의 Memory 공간을 할당하는 Process
*   Memory 할당은 주로 Computer H/W 작업이지만 OS 운영체제 및 S/W 응용 Programme을 통해 관리

#### Dynamic Memory Allocation Function 동적 메모리 할당 함수

`malloc` **(Memory Allocation)**
*   Memory 할당후 "포인터(주소값)"으로 "Return"

➝ Return 값 = 할당된 Memory의 0번째 주소값

*   포인터(주소값)으로 부터 n Bytes의 Memory 할당
*   할당된 Memory 내 "쓰레기값" 존재할 수 있음

`calloc` **(Contiguous Allocation)**
*   Memory 할당후 "포인터(주소값)"으로 "Return"

➝ Return 값 = 할당된 Memory의 0번째 주소값

*   포인터(주소값)으로 부터 n Bytes의 Memory 할당
*   할당된 Memory 내 정수 "0"으로 초기화

`realloc` **(Re-Allocation)**
*   이미 할당된 Memory 크기 변경
*   malloc / calloc 함수 "선"사용

`free`
*   할당된 Memory 해제

## **Example)**

`malloc` **(Memory Allocation)**
**return\_heap\_1.c**
수강생 학번 입력

```cpp
#include <stdio.h>
#include <stdlib.h>

int *Module_Participant(int Student_Count)
{
    int *Memory_Address = malloc(Student_Count * sizeof(int));   // E.g.)  Student_Count = 10명 ➝ int 메모리 10개 할당 (10명 x 4 Bytes)
                                                                 //        malloc 반환값 = 할당된 메모리 0번째 주소값
    
    return Memory_Address;                                       // Memory_Address = malloc 반환값 = 할당된 메모리 0번째 주소값
}

// int *Module_Participant(int Student_Count)
// {
//     return malloc(Student_Count * sizeof(int));                                     
// }

int main()
{
    int *Class_Participant;
    int Student_Number;

    printf("Input Student Number: ");
    scanf("%d", &Student_Number);

    Class_Participant = Module_Participant(Student_Number);

    for (int i = 0; i < Student_Number; i++)
    {
        printf("Student_ID: %d\n", Class_Participant + i);     // Class_Participant + i (i = 0 ~ Student_Number -1) ➝ 할당된 메모리 0번째 주소값 ~ (Student_Number - 1)번째 주소값
        printf("Student_ID: %d\n", *(Class_Participant + i));  // *(Class_Participant + i)* = Class_Participant[i] (i = 0 ~ Student_Number -1) = 주소값이 가르키는 값 ➝ 쓰레기값 있을수 있음 
    }
    for (int i = 0; i < Student_Number; i++)
    {
        scanf("%d", Class_Participant + i);                    // Class_Participant + i (i = 0 ~ Student_Number -1) ➝ 할당된 메모리 0번째 주소값 ~ (Student_Number - 1)번째 주소값"에" 입력값(학번) 초기화
                                                               // 주소값"에": e.g.) scanf("%d", &X); ➝ 변수 X 주소값"에" 초기화 (= 변수 X 주소값"을 시작으로" 초기화)    
    }
    for (int i = 0; i < Student_Number; i++)
    {
        printf("Student_Id: %d\n", *(Class_Participant + i));  // *(Class_Participant + i)* = Class_Participant[i] (i = 0 ~ Student_Number -1) = 주소값이 가르키는 값 ➝ 초기화값(학번) 출력  
    }

    return 0;
}


```

`calloc` **(Contiguous Allocation)**
**return\_heap\_2.c**
수강생 학번 입력

```perl
#include <stdio.h>
#include <stdlib.h>

int *Module_Participant(int Student_Count)
{
    return calloc(Student_Count, sizeof(int));                                     
}

int main()
{
    int *Class_Particiapnt;
    int Student_Number;

    printf("Input Student Number: ");
    scanf("%d", &Student_Number);

    Class_Particiapnt = Module_Participant(Student_Number);

    for (int i = 0; i < Student_Number; i++)
    {
        printf("Student_ID: %d\n", Class_Particiapnt + i);     // Class_Particiapnt + i (i = 0 ~ Student_Number -1) ➝ 할당된 메모리 0번째 주소값 ~ (Student_Number - 1)번째 주소값
        printf("Student_ID: %d\n", *(Class_Particiapnt + i));  // *(Class_Particiapnt + i)* = Class_Particiapnt[i] (i = 0 ~ Student_Number -1) = 주소값이 가르키는 값 ➝ 0으로 초기화
    }
    for (int i = 0; i < Student_Number; i++)
    {
        scanf("%d", Class_Particiapnt + i);                    // Class_Particiapnt + i (i = 0 ~ Student_Number -1) ➝ 할당된 메모리 0번째 주소값 ~ (Student_Number - 1)번째 주소값"에" 입력값(학번) 초기화
                                                          // 주소값"에": e.g.) scanf("%d", &X); ➝ 변수 X 주소값"에" 초기화 (= 변수 X 주소값"을 시작으로" 초기화)    
    }
    for (int i = 0; i < Student_Number; i++)
    {
        printf("Student_Id: %d\n", *(Class_Particiapnt + i));  // *(Class_Particiapnt + i)* = Class_Particiapnt[i] (i = 0 ~ Student_Number -1) = 주소값이 가르키는 값 ➝ 초기화값(학번) 출력  
    }

    return 0;
}


```

`malloc` **(Memory Allocation) vs** `calloc` **(Contiguous Allocation)**
쓰레기값초기화 vs 정수 0 초기화
**return\_heap\_3.c**
수강생 학번 입력\_Build-Up #1

```cpp
#include <stdio.h>
#include <stdlib.h>

int *Module_A(int student_count)
{
    return malloc(student_count * sizeof(int));
}

int *Module_B(int student_count)
{
    return calloc(student_count, sizeof(int));
}

int main()
{
    int *Class_A;
    int *Class_B;
    int Student_n_A;
    int Student_n_B;

    printf("Input Student Number A: ");
    scanf("%d", &Student_n_A);
    printf("Input Student Number B: ");
    scanf("%d", &Student_n_B);

    Class_A = Module_A(Student_n_A);
    Class_B = Module_B(Student_n_B);

    printf("\nClass_A: \n");
    for (int i = 0; i < Student_n_A; i++)
    {
        printf("Class A Address: %d\n", Class_A + i);
        printf("Subject A - Default ID#: %d\n", *(Class_A + i));
    }
    printf("\nClass_B: \n");
    for (int i = 0; i < Student_n_B; i++)
    {
        printf("Class B Address: %d\n", Class_B + i);
        printf("Subject B - Default ID#: %d\n", *(Class_B + i));
    }

    printf("\nInput Class A ID#: \n");
    for (int i = 0; i < Student_n_A; i++)
    {
        scanf("%d", Class_A + i);
    }
    printf("\nInput Class B ID#: \n");
    for (int i = 0; i < Student_n_B; i++)
    {
        scanf("%d", Class_B + i);
    }

    printf("\nClass_A ID#: \n");
    for (int i = 0; i < Student_n_A; i++)
    {
        printf("Subject A - ID#: %d\n", *(Class_A + i));
    }
    printf("\nClass_B ID#: \n");
    for (int i = 0; i < Student_n_B; i++)
    {
        printf("Subject B - ID#: %d\n", *(Class_B + i));
    }

    return 0;
}


```

**return\_heap\_4.c**
수강생 학번 입력\_Build-Up #2

```cpp
#include <stdio.h>
#include <stdlib.h>

// 3) 생성된 Class A, B 요소(학생)수로 Class A, B Memory 할당 및 주소값 생성
int *Module_A(int Class_n_A)
{
    return malloc(Class_n_A * sizeof(int));
}
int *Module_B(int Class_n_B)
{
    return calloc(Class_n_B, sizeof(int));
}

// 4) 인수 ➝ 매개변수 초기화로 Class A, B ID# 입력 및 출력
void Set_ID(int *ID_A, int *ID_B, int ID_n_A, int ID_n_B)
{
    printf("\nInput ID# for Class A: \n");
    for (int i = 0; i < ID_n_A; i++)
    {
        scanf("%d", ID_A + i);
    }
    printf("Input ID# for Class B: \n");
    for (int i = 0; i < ID_n_B; i++)
    {
        scanf("%d", ID_B + i);
    }

    printf("\nA List of ID# for Class A: \n");
    for (int i = 0; i < ID_n_A; i++)
    {
        printf("%d\n", *(ID_A + i));
    }
    printf("A List of ID# for Class B: \n");
    for (int i = 0; i < ID_n_B; i++)
    {
        printf("%d\n", *(ID_B+ i));
    }
}

int main()
{   
    // 1) Class A, B Memory 주소값 + Class A, B 요소(학생)수
    int *Class_A;
    int *Class_B;
    int Class_n_A;
    int Class_n_B;

    // 2) Class A, B 요소(학생)수 생성
    printf("Input the Number of Students for Class A: \n");
    scanf("%d", &Class_n_A);
    printf("Input the Number of Students for Class B: \n");
    scanf("%d", &Class_n_B);

    // 3) 생성된 Class A, B Memory 주소값 초기화  ➝  58번째줄 함수 호출을 위한 인수 생성
    Class_A = Module_A(Class_n_A);
    Class_B = Module_B(Class_n_B);

    // 4) 생성된 인수(주소값, 요소수)로 Class A, B ID# Set-up 함수 호출
    Set_ID(Class_A, Class_B, Class_n_A, Class_n_B);

    return 0;
}


```

**return\_heap\_5.c**
수강생 학번 입력\_Build-Up #3

```cpp
#include <stdio.h>
#include <stdlib.h>

int *Module_A(int *Module_A_Size)
{
    scanf("%d", Module_A_Size);

    return malloc((*Module_A_Size) * sizeof(int));
}
int *Module_B(int *Module_B_Size)
{
    scanf("%d", Module_B_Size);

    return calloc((*Module_B_Size), sizeof(int));
}

void Set_ID(int *ID, int ID_n)   // 매개변수가 2개 1 Set ➝ n개 Set로 확장될 경우, 54~62번째줄 처럼  동일 사용자정의 함수를 메인함수에서 반복(A반 호출, B반 호출)해서 실행하면 됨
{

    for (int i = 0; i < ID_n; i++)
    {
        scanf("%d", ID + i);
    }
}
void Print_ID(int *ID, int ID_n) // 매개변수가 2개 1 Set ➝ n개 Set로 확장될 경우, 54~62번째줄 처럼  동일 사용자정의 함수를 메인함수에서 반복(A반 호출, B반 호출)해서 실행하면 됨
{

    for (int i = 0; i < ID_n; i++)
    {
        printf("%d\n", *(ID + i));
    }
}

int main()
{
    int *Class_A;
    int *Class_B;

    int Class_A_Size;
    int Class_B_Size;

    // Previously,  "수강생 학번 입력_Build-Up #1 ~ #2" 에서 scanf Code를 메인 함수 내에 작성할 수 밖에 없었던 이유
    // ⭢  동적할당 메모리 함수(49~52번째줄)를 호출하기 위해 인수값을 39~40번째줄 변수 Class_A_Size, Class_B_Size의 초기화값으로 사용해야 했음
    // ⭢  Class_A_Size, Class_B_Size에 초기화하기 위해 scanf 함수를 변수 선언(39~40번째줄)과 사용자정의 함수(4~15번째줄) 호출 사이에 작성해야 했음
    // Currently,  "수강생 학번 입력_Build-Up #3"에서        scanf Code를 사용자정의 함수(4~15번째줄) 내에 사용하기 위해 
    // ⭢  동적할당 메모리 함수(49~52번째줄)를 호출하기 위해 인수값을 39~40번째줄 변수 Class_A_Size, Class_B_Size의 초기화값으로 사용하지 않고
    // ⭢  변수 Class_A_Size, Class_B_Size의 주소값으로 사용하여
    // ⭢  scanf의 개념이 "주소값을 시작으로 또는 주소값에 초기화"이므로,  사용자정의 함수(4~15번째줄) 매개변수를 주소값으로 받아 scanf로 초기화 가능해짐
    printf("Input the Number of Studnets for Class A: \n");
    Class_A = Module_A(&Class_A_Size);
    printf("Input the Number of Studnets for Class B: \n");
    Class_B = Module_B(&Class_B_Size);

    printf("\nInput ID# for Class A: \n");
    Set_ID(Class_A, Class_A_Size);
    printf("\nA List of ID# for Class A: \n");
    Print_ID(Class_A, Class_A_Size);

    printf("\nInput ID# for Class B: \n");
    Set_ID(Class_B, Class_B_Size);
    printf("\nA List of ID# for Class B: \n");
    Print_ID(Class_B, Class_B_Size);

    return 0;
}


```

⇓ In which Case **malloc or calloc** is Used

| malloc | calloc |
| ---| --- |
| E.g.)<br>회원가입<br>항목 #1 필수<br>항목 #2 필수<br>항목 #3 필수<br>항목 #4 필수<br>항목 #5 필수<br><br>➝ 항목 #1 ~ 5까지 필수 입력하기 때문에<br>해당 Memory에 입력값이 덮어쓰기 되어<br>쓰레기값이 있어도 좋음 | E.g.)<br>회원가입<br>항목 #1 필수<br>항목 #2 필수<br>항목 #3 필수<br>항목 #4 선택<br>항목 #5 선택<br><br>➝ 항목 #4 ~ 5까지 선택 입력하기 때문에<br>해당 Memory에 입력값이 덮어쓰기 되지않아<br>0으로 초기화되면 좋음 |

**return\_heap\_6.c**
malloc: 쓰레기값초기화
회원가입

```cpp
#include <stdio.h>
#include <stdlib.h>



```

**return\_heap\_7.c**
calloc: 정수 0 초기화
회원가입

```cpp
#include <stdio.h>
#include <stdlib.h>


         
```

**return\_heap\_8.c**
시간차 계산기
Theoretically
*   malloc: 0으로 초기화하지 않기 때문에 시간 소모 작음
*   calloc: 0으로 초기화하기 하기 때문에 시간 소모 큼
Pragmatically
*   시간소모 차이 크기 않음
※ 각각 동적메모리 함수 반복 실행 수행 경우
Computer는 Code를 기억/처리/저장(≒ Cashing 캐쉬처리)하고 있기 때문에 시간 줄어음

```plain
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <sys/time.h>
#include <unistd.h>

int main()
{
    struct timeval tv;         // #include <sys/time.h> 라이버러리 내에 timeval 명의 구조체 존재
    double begin, end;         // float보다 큰 자료형 (8 Bytes)
    
    // Frame #1
    // 시작하는 시간 받아오기
    gettimeofday(&tv, NULL);   // #include <sys/time.h> 라이버러리 내에 gettimeofday 함수 존재:  함수를 사용하여 구조체 tv내의 속성값 초기화
    begin = (tv.tv_sec) * 1000 + (tv.tv_usec) / 1000;  // "." = ~의, ~내의:  구조체 tv 내의 속성값중 tv_sec 값, 구조체 tv 내의 속성값중 tv_usec 값

    // 시간 측정을 진행할 부분
    int *Time;
    int Time_Count = 99999; 


    Time = malloc(Time_Count * sizeof(int));
    // Time = calloc(Time_Count, sizeof(int));

    for (int i = 0; i < Time_Count; i++)              // 25~29번째줄 Code가 없는 경우, 22 or 23번째줄에서 할당후에 Time 변수를 더이상 사용하지 않기 때문에 컴파일시 할당 자체를 하지 않음
    {
        *(Time + i) = i;                              //    27번째줄 Code가 있는 경우, 22 or 23번째줄에서 할당후에 어차피 초기화하기 때문에 컴파일시 malloc으로 처리할 수도 있음
                                                      //    27번째줄 Code가 없는 경우, 22 or 23번째줄에서 할당후에 초기화하지 않기 때문에 컴파일시 calloc으로 처리할 수도 있음
        printf("%d, %d\n", i, *(Time + i));
    }

    // Frame #2
    // 끝나는 시간 받아오기
    gettimeofday(&tv, NULL);
    end = (tv.tv_sec) * 1000 + (tv.tv_usec) / 1000;

    // 출력
    printf("Execution time %f\n", (end - begin) / 1000);

    return (0);
}


```

`realloc` **(Re-Allocation)**
**return\_heap\_9.c**
수강생 학번 입력\_Build-Up #1

```cpp
#include <stdio.h>
#include <stdlib.h>

int *Module_A(int Module_n_A)
{
    return calloc(Module_n_A, sizeof(int));
}
int *Module_B(int Module_n_B)
{
    return calloc(Module_n_B, sizeof(int));
}

void Extend_A(int *Moudule_A, int Module_n_A)
{
    Moudule_A = realloc(Moudule_A, Module_n_A * sizeof(int));
    return; 
}
void Extend_B(int *Moudule_B, int Module_n_B)
{
    Moudule_B = realloc(Moudule_B, Module_n_B * sizeof(int));
    return; 
}

void Set_ID(int *ID_A, int *ID_B, int ID_n_A, int ID_n_B)
{
    printf("\nInput ID# for Class A: \n");
    for (int i = 0; i < ID_n_A; i++)
    {
        scanf("%d", ID_A + i);
    }
    printf("Input ID# for Class B: \n");
    for (int i = 0; i < ID_n_B; i++)
    {
        scanf("%d", ID_B + i);
    }

    printf("\nA List of ID# for Class A: \n");
    for (int i = 0; i < ID_n_A; i++)
    {
        printf("%d\n", *(ID_A + i));
    }
    printf("A List of ID# for Class B: \n");
    for (int i = 0; i < ID_n_B; i++)
    {
        printf("%d\n", *(ID_B+ i));
    }
}

int main()
{   
    int *Class_A;
    int *Class_B;
    int Class_n_A;
    int Class_n_B;
    
    int Extend_n_A;
    int Extend_n_B;

    // Relloc 전
    printf("Input the Number of Students for Class A: \n");
    scanf("%d", &Class_n_A);
    printf("Input the Number of Students for Class B: \n");
    scanf("%d", &Class_n_B);

    Class_A = Module_A(Class_n_A);
    Class_B = Module_B(Class_n_B);

    Set_ID(Class_A, Class_B, Class_n_A, Class_n_B);

    printf("\n============================================= \n");
    
    // Relloc 후
    printf("\nInput the Add Number of Students for Class A: \n");
    scanf("%d", &Extend_n_A);
    printf("Input the Add Number of Students for Class B: \n");
    scanf("%d", &Extend_n_B);

    Extend_A(Class_A, Class_n_A + Extend_n_A);
    Extend_B(Class_B, Class_n_A + Extend_n_B);

    Set_ID(Class_A, Class_B, Class_n_A + Extend_n_A, Class_n_B + Extend_n_B);

    return 0;
}


```

**return\_heap\_10.c**
수강생 학번 입력\_Build-Up #2

```plain
#include <stdio.h>
#include <stdlib.h>

int *Module_Type(int *Module_Type_Size)
{
    scanf("%d", Module_Type_Size);

    return calloc((*Module_Type_Size), sizeof(int));
}

void Extend_Type(int *Moudule_Type, int Module_Type_Size, int *Extend_Type_Size)
{
    scanf("%d", Extend_Type_Size);

    Moudule_Type = realloc(Moudule_Type, (Module_Type_Size + *Extend_Type_Size) * sizeof(int));

    return;
}

void Set_ID(int *ID, int ID_n)
{
    for (int i = 0; i < ID_n; i++)
    {
        scanf("%d", ID + i);
    }
}
void Print_ID(int *ID, int ID_n)
{
    for (int i = 0; i < ID_n; i++)
    {
        printf("%d\n", *(ID + i));
    }
}
int main()
{
    int *Class_A;
    int *Class_B;
    int Class_A_Size;
    int Class_B_Size;

    // Relloc 전
    printf("Input the Number of Students for Class A: \n");
    Class_A = Module_Type(&Class_A_Size);
    printf("Input the Number of Students for Class B: \n");
    Class_B = Module_Type(&Class_B_Size);

    printf("\nInput ID# for Class A: \n");
    Set_ID(Class_A, Class_A_Size);
    printf("\nA List of ID# for Class A: \n");
    Print_ID(Class_A, Class_A_Size);

    printf("\nInput ID# for Class B: \n");
    Set_ID(Class_B, Class_B_Size);
    printf("\nA List of ID# for Class B: \n");
    Print_ID(Class_B, Class_B_Size);

    printf("\n============================================= \n");

    // Relloc 후
    int Extend_A_Size;
    int Extend_B_Size;

    // scanf Code를 사용자정의 함수(11~18번째줄) 내에 사용하기 위한 Code Specificataion 원리:  i_pointer_func_4.c 파일(malloc/calloc 사용한 "수강생 학번 입력_Build-Up #2") 참조
    printf("\nInput the Add Number of Students for Class A: \n");
    Extend_Type(Class_A, Class_A_Size, &Extend_A_Size);
    printf("\nInput the Add Number of Students for Class B: \n");
    Extend_Type(Class_B, Class_B_Size, &Extend_B_Size);

    printf("\nInput ID# for Class A: \n");
    Set_ID(Class_A, Class_A_Size + Extend_A_Size);
    printf("\nA List of ID# for Class A: \n");
    Print_ID(Class_A, Class_A_Size + Extend_A_Size);

    printf("\nInput ID# for Class B: \n");
    Set_ID(Class_B, Class_B_Size + Extend_B_Size);
    printf("\nA List of ID# for Class B: \n");
    Print_ID(Class_B, Class_B_Size + Extend_B_Size);

    return 0;
}


```

**return\_heap\_11.c**
수강생 학번 입력\_Build-Up #3
*   입력: "확장"된 Memory 주소값 부터
*   출력: "선언"된 Memory 주소값 부터 ("0번째" 주소값 부터)

```plain
#include <stdio.h>
#include <stdlib.h>

int *Module_Type(int *Module_Type_Size)
{
    scanf("%d", Module_Type_Size);

    return calloc((*Module_Type_Size), sizeof(int));
}

void Extend_Type(int *Moudule_Type, int Module_Type_Size, int *Extend_Type_Size)
{
    scanf("%d", Extend_Type_Size);

    Moudule_Type = realloc(Moudule_Type, (Module_Type_Size + *Extend_Type_Size) * sizeof(int));

    return;
}

void Set_ID(int *ID, int ID_n)
{
    for (int i = 0; i < ID_n; i++)
    {
        scanf("%d", ID + i);
    }
}
void Print_ID(int *ID, int ID_n)
{
    for (int i = 0; i < ID_n; i++)
    {
        printf("%d\n", *(ID + i));
    }
}
int main()
{
    int *Class_A;
    int *Class_B;
    int Class_A_Size;
    int Class_B_Size;

    // Relloc 전
    printf("Input the Number of Students for Class A: \n");
    Class_A = Module_Type(&Class_A_Size);
    printf("Input the Number of Students for Class B: \n");
    Class_B = Module_Type(&Class_B_Size);

    printf("\nInput ID# for Class A: \n");
    Set_ID(Class_A, Class_A_Size);
    printf("\nA List of ID# for Class A: \n");
    Print_ID(Class_A, Class_A_Size);

    printf("\nInput ID# for Class B: \n");
    Set_ID(Class_B, Class_B_Size);
    printf("\nA List of ID# for Class B: \n");
    Print_ID(Class_B, Class_B_Size);

    printf("\n============================================= \n");

    // Relloc 후
    int Extend_A_Size;
    int Extend_B_Size;

    printf("\nInput the Add Number of Students for Class A: \n");
    Extend_Type(Class_A, Class_A_Size, &Extend_A_Size);
    printf("\nInput the Add Number of Students for Class B: \n");
    Extend_Type(Class_B, Class_B_Size, &Extend_B_Size);

    // 사용자정의 함수(Set_ID, Print_ID)의 인수 값이 " 수강생 학번 입력_Build-Up #2"와 달라짐
    // ⭢   확장된 Memory 주소값 부터 입력하고,  선언된 Memory 주소값 부터 (0번째 주소값 부터) 출력하기 위해 아래 사용자정의 함수(71~79번째줄)의 인수 "수정"함
    // Ref) "수정":   포인터변수 연산을 활용하여  확장된 Memory 시작 주소값 (0번째 주소값을 지정할 수 있음
    printf("\nInput ID# for Class A: \n");
    Set_ID(Class_A + Class_A_Size, Extend_A_Size);
    printf("\nA List of ID# for Class A: \n");
    Print_ID(Class_A, Class_A_Size + Extend_A_Size);

    printf("\nInput ID# for Class B: \n");
    Set_ID(Class_B + Class_B_Size, Extend_B_Size);
    printf("\nA List of ID# for Class B: \n");
    Print_ID(Class_B, Class_B_Size + Extend_B_Size);
    // 만약 "수강생 학번 입력_Build-Up #1"에서 Set_ID, Print_ID 함수가 구분되어 있지 않았다면,
    // 70번째줄과 72번째줄,  75번째줄과 77번째줄의 매개변수가 다르기 때문에, 여기 "수강생 학번 입력_Build-Up #3"에서 사용자정의 함수를 수정(구분) 했어야함
    // 하지만, "수강생 학번 입력_Build-Up #2"에서 구분했기때문에, "수강생 학번 입력_Build-Up #3"에서는 사용자정의함수는 수정하지 않았고, 메인 함수(71~79번째줄)의 인수만 수정
    // 따라서, 함수 1개당 기능 1개의 권장사항을 지키는 것이 Code를 Update하는데 좋음

    return 0;
}


```

`free`
**return\_heap\_12.c**
수강생 학번 입력: free 사용 O ➝ HEAP Overflow 발생 X

```cpp
#include <stdio.h>
#include <stdlib.h>

int *Module_A(int *Module_A_Size)
{
    scanf("%d", Module_A_Size);

    return malloc((*Module_A_Size) * sizeof(int));
}
int *Module_B(int *Module_B_Size)
{
    scanf("%d", Module_B_Size);

    return calloc((*Module_B_Size), sizeof(int));
}

void Set_ID(int *ID, int ID_n)
{   
    for (int i = 0; i < ID_n; i++)
    {
        scanf("%d", ID + i);
    }
}
void Print_ID(int *ID, int ID_n) 
{
    for (int i = 0; i < ID_n; i++)
    {
        printf("%d\n", *(ID + i));
    }
}

int main()
{
    int *Class_A;
    int *Class_B;

    int Class_A_Size;
    int Class_B_Size;

    printf("Input the Number of Studnets for Class A: \n");
    Class_A = Module_A(&Class_A_Size);
    printf("Input the Number of Studnets for Class B: \n");
    Class_B = Module_B(&Class_B_Size);

    printf("\nInput ID# for Class A: \n");
    Set_ID(Class_A, Class_A_Size);
    printf("\nA List of ID# for Class A: \n");
    Print_ID(Class_A, Class_A_Size);

    printf("\nInput ID# for Class B: \n");
    Set_ID(Class_B, Class_B_Size);
    printf("\nA List of ID# for Class B: \n");
    Print_ID(Class_B, Class_B_Size);

    free(Class_A);
    printf("\nA List of ID# for Class A: \n");
    Print_ID(Class_A, Class_A_Size);
    free(Class_B);
    printf("\nA List of ID# for Class B: \n");
    Print_ID(Class_B, Class_B_Size);

    return 0;
}


```

**return\_heap\_13.c**
수강생 학번 입력: free 사용 X ➝ HEAP Overflow 발생 O

```cpp
#include <stdio.h>
#include <stdlib.h>

int *Module_A(int *Module_A_Size)
{
    return malloc((*Module_A_Size) * sizeof(int));
}
int *Module_B(int *Module_B_Size)
{
    return calloc((*Module_B_Size), sizeof(int));
}

void Set_ID(int *ID, int ID_n)  
{
    for (int i = 0; i < ID_n; i++)
    {
        *(ID + i) = i;
    }
}
void Print_ID(int *ID, int ID_n) 
{

    for (int i = 0; i < ID_n; i++)
    {
        // printf("%d\n", *(ID + i));
    }
}

int main()
{
    int *Class_A;
    int *Class_B;

    int Class_A_Size = 100;
    int Class_B_Size = 100;

    int i = 0;
    while (1)
    {
        // printf("Input the Number of Studnets for Class A: \n");
        Class_A = Module_A(&Class_A_Size);
        // printf("Input the Number of Studnets for Class B: \n");
        Class_B = Module_B(&Class_B_Size);

        // printf("\nInput ID# for Class A: \n");
        Set_ID(Class_A, Class_A_Size);
        // printf("\nA List of ID# for Class A: \n");
        Print_ID(Class_A, Class_A_Size);

        // printf("\nInput ID# for Class B: \n");
        Set_ID(Class_B, Class_B_Size);
        // printf("\nA List of ID# for Class B: \n");
        Print_ID(Class_B, Class_B_Size);

        i++;
        printf("======%d======\n", i);
    }

    return 0;
}


```