# [CH03L] Operator (Lecture)

## **C Language Learning Road Map**

> 데이터 형식 종류 ➝ 데이터 입력/출력 방식/원리 ➝ 다양한 처리과정

![](https://t9003081320.p.clickup-attachments.com/t9003081320/9ffdfbf7-497a-4a5e-ac73-07ec85a51eea/Picture1.png)

# **Operator 연산자**

컴퓨터가 해당언어(C Language)로 자료(Data)를 처리하는 방식

Arithmetic, Assignment, Type Conversion, Relational, Logical, Condition, Comma, Bitwise

Precondition 전제조건
\* Computing → Programme Code Processing Flow 프로그램 코드 실행 순서

`Window OS`

TEMP 작동 O → 주소값 관련
*   scanf 함수 사용 시 시작 → &변수
*   배열 선언 시 시작 → 배열내 주소값 저장
*   증감 후위 연산 시 시작 → 변수 초기화 선행 (e.g. A++, A--)

연산 작동
CPU 레지스트리 내 작동
int 정수(2진수, 8진수, 16진수, 10진수) 기반

## **Input 입력**

`Window OS` (연산시) 왼쪽 ← 오른쪽 Compiling

X 방식(TEMP 작동 O) = scanf 함수 사용 O(선언 '후' 초기화)
메모리박스 내 TEMP 초기화 O
→ 메모리박스 내 TEMP 0, TEMP 1, TEMP 2 ... 각각 초기화
→ TEMP 0, TEMP 1, TEMP 2 ... 초기화된 변수 메모리박스 내 각각 초기화
E.g.)
int A;
scanf("%d", &A);
메모리박스 내 TEMP A0, TEMP A1, TEMP A2 ... 각각 초기화
TEMP A0, TEMP A1, TEMP A2 ... 초기화된 변수 메모리박스 내 각각 초기화

![](https://t9003081320.p.clickup-attachments.com/t9003081320/4692901f-3413-47dc-bc0a-96b12262f1b8/Picture3.png)
E.g.)
int A = 7 (정수)
A++, A-- 증감 후위 연산자: 1) 초기화 '후' 2) 연산

Y 방식(TEMP 작동 X) = scanf 함수 사용 X(선언 '동시' 초기화)
메모리박스 내 TEMP 초기화 X
→ 메모리박스 내 덮어쓰기 초기화
→ 최종 초기화된 변수 메모리박스 내 최종 초기화

![](https://t9003081320.p.clickup-attachments.com/t9003081320/99605586-267d-4e8e-8cf8-f40e34304ce7/Picture4.png)
E.g.)
int A = 정수
++A, --A 증감 전위 연산자: 1) 연산 '후' 2) 초기화

**Case)**

증감 후위연산자 (A++, A--)
증감 전위연산자 (++A, --A)
대입 연산자 (A+=B, A-=B, A\*=B, A/B, A%B)

선언 '동시' 초기화 = scanf 함수 사용 X = Y 방식(TEMP 작동 X)

*   변수 1개

증감 후위연산자: X 방식(TEMP 작동 O)

증감 전위연산자: Y 방식(TEMP 작동 X)

증감 후위연산자: X 방식(TEMP 작동 O) + 증감 전위연산자: Y 방식(TEMP 작동 X)

대입 연산자: 無 →Y 방식(TEMP 작동 X)

*   배열 X 방식(TEMP 작동 O)

증감 후위연산자: X 방식(TEMP 작동 O)

증감 전위연산자: Y 방식(TEMP 작동 X) → X 방식(TEMP 작동 O)

증감 후위연산자: X 방식(TEMP 작동 O) + 증감 전위연산자: X 방식(TEMP 작동 O)

대입 연산자: 無 →X 방식(TEMP 작동 O)

선언 '후' 초기화 = scanf 함수 사용 O = X 방식(TEMP 작동 O)

*   변수 1개

증감 후위연산자: X 방식(TEMP 작동 O)

증감 전위연산자: Y 방식(TEMP 작동 X) → X 방식(TEMP 작동 O)

증감 후위연산자: X 방식(TEMP 작동 O) + 증감 전위연산자: X 방식(TEMP 작동 O)

대입 연산자: 無 → X 방식(TEMP 작동 O)

*   배열 X 방식(TEMP 작동 O)

증감 후위연산자: X 방식(TEMP 작동 O)

증감 전위연산자: Y 방식(TEMP 작동 X) → X 방식(TEMP 작동 O)

증감 후위연산자: X 방식(TEMP 작동 O) + 증감 전위연산자: X 방식(TEMP 작동 O)

대입 연산자: 無 → X 방식(TEMP 작동 O)

※ `TEMP` 작동원리

하나라도 X 방식(TEMP 작동 O) in 초기화 Track → X 방식(TEMP 작동 O) 초기화

E.g.)
선언 '동시' 초기화 \[Y 방식(TEMP 작동 X)\]
→ 변수 갯수 1개
→ 증감 후위 연산자 \[X 방식(TEMP 작동 O)\]
\= X 방식(TEMP 작동 O) 초기화
E.g.)
선언 '동시' 초기화 \[Y 방식(TEMP 작동 X)\]
→ 배열 \[X 방식(TEMP 작동 O)\]
→ 증감 전위 연산자 \[Y 방식(TEMP 작동 X)\]
\= X 방식(TEMP 작동 O) 초기화

![](https://t9003081320.p.clickup-attachments.com/t9003081320/ed446cd9-06db-4738-82b3-60112c576f43/0_temp_working_principle_1.png)

![](https://t9003081320.p.clickup-attachments.com/t9003081320/7f44e632-e346-4f4a-81c0-a713e9483c84/0_temp_working_principle_2.png)

`Mac OS` 왼쪽 → 오른쪽 Compiling

X 방식(TEMP 작동 O)

* * *

### **Basic**

Arithmetic & Assingment ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2398](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2398))

Type Conversion ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2418](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2418))

Relational ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2438](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2438))

Logical ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2458](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2458))

Condition ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2478](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2478))

Comma ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2498](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2498))

Bitwise ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2518](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-2518))

* * *

### **Advanced**

Computer Architecture & Temp ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-4358](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-4358))

Floating Point Binary Calculation ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-4378](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-4378))