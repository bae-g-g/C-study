# Call by Address (② Pointer Variable = Parameter + Return)

## **Call by Address**
## **→ Return = Pointer Variable**
사용자정의 함수 (반환 = 포인터변수)

#### Prerequisite Understanding

Memory (Management + Structure + Operation) ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-6338](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-6338))

Memory (Compile & Run Time) ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-6358](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-6358))

* * *

### **Significance 의의**

Premise Condition
❶ 사용자정의 함수 사용
❷ 사용자정의 함수 종료후에도 외부에 정의된 함수의 변수값 초기화/변경할 경우
※ 사용자정의 함수 사용 이유
*   Simplify Main Function Code 메인 함수 코드 간소화
*   Useful for Code Modification & Extension 코드 수정 및 확장 용이

**① 배열을 Return (반환)할 경우**
배열 X (➝붕괴➝ 포인터변수 &X\[0\])

Return 포인터변수 자료 3가지 형태
*   Auto
*   Static
*   By Dynamic Memory Allocation

Problem
*   "Auto" (e.g. Local Variable 지역변수) + 포인터변수

⇒ STACK Sector "할당" = Run Time 시 할당 (Code Block 실행 중 할당)

⇒ Life Cycle 사용자정의 함수 실행 ~ 사용자정의 함수 종료

①A 배열(배열이 붕괴된 포인터변수) 반환 "조차" 가능 X

E.g.) return X; // int X\[3\]; : X ➝(붕괴 O)➝ &X\[0\]

➝ 0 반환

∵ Compiling Error #1: 배열 재초기화 불가능

(Return=다른함수 변수 재초기화) ➝(배열 적용)➝ (Return=다른함수 배열 재초기화)

E.g.)

int A\[3\] = {1, 2, 3}; // ≒ Return 값

int B\[3\] = A; //  Compiling Error O

∵ Compiling Error #2: C언어 없는 기능 설정

배열 크기가 너무 크면 함수에서 처리시 너무 비효율적이므로 없는 기능 설정

①B 포인터변수 반환"은" 가능 O

E.g.) return X\_ptr; // int X\[3\]; : int \*X\_ptr = &X\[0\];

② 사용 범위가 지역 변수 (함수 내)

③ Life Cycle이 사용자정의 함수 종료후 포인터변수 Memory "해제"

i.e. ①AB + ② + ③

사용자정의 함수 종료후

해당 Memory 공간에 다른 변수/함수 (e.g. 반복문 int i , printf) "할당" 확율 있음

∵ Stack Sector 메모리 "할당" 원리(Stack 쌓임) 특성

∴ 사용자정의 함수 Return (반환)한 포인터변수(주소값)으로 접근한 메모리 공간

≠ 배열 메모리 공간

本 의도한 초기화값 (e.g. 배열 요소 값)
≠ 실제 배열 메모리 공간에 초기화된 값 (e.g. 사용자정의 함수호출 아래 i 값, printf 주소값)
⇓
Solution #1
*   "Static" 정적변수 + 포인터변수

⇒ DATA Sector "할당" = Compile 시 할당 (Run Time시 RAM에 복사/할당 실행)

⇒ Life Cycle 변수 선언된 Code Block 시작 ~ Programme 종료 (Run Time 중 계속 유지)

① 포인터변수 반환 가능 O

② 사용 범위가 지역 변수 (함수 내)

③ Life Cycle이 사용자정의 함수 종료후 포인터변수 Memory "유지"

i.e. ① + ② + ③

사용자정의 함수가 종료되어도

Life Cycle이 유지되는 Static 정적변수로 포인터변수(주소값)을 Return (반환)하여

메인 함수의 배열에 접근 가능 O

∴ 사용자정의 함수 Return (반환)한 포인터변수(주소값)으로 접근한 메모리 공간

\= 배열 메모리 공간

本 의도한 초기화값 (e.g. 배열 요소 값)

\= 실제 배열 메모리 공간에 초기화된 값 (e.g. 배열 요소 값)

Ref) 큰변수(e.g. 배열, 구조체, 클라스) + static 포인터변수 사용 의의

변수의 크기가 크기 때문에 변수 전체를 사용하기 보다 주소값만으로 접근함이 용이

+
Solution #2
*   "Dynamic Memory Allocation" 동적 메모리 할당

下 2) 참조

**② Dynamic Memory Allocation 동적 메모리 "할당"후 "할당"된 Memory 주소값 Return (반환)**
⇒ HEAP Sector "할당" = Run Time 시 할당 (Programme 실행 중 할당)
⇒ Life Cycle 변수 선언된 Code Block 시작 ~ Programme 종료 (Run Time 중 계속 유지)
사용자가 직접 할당하는 함수(malloc, calloc, relloc)의 Return (반환)
\= 포인터변수(주소값)
① 포인터변수 반환 가능 O
② 사용 범위가 지역 변수 (함수 내)
③ Life Cycle이 사용자정의 함수 종료후 포인터변수 Memory "유지"
i.e. ① + ② + ③

사용자정의 함수가 종료되어도

Life Cycle이 유지되는 동적 메모리 할당으로 포인터변수(주소값)을 Return (반환)하여

메인 함수의 배열에 접근 가능 O

∴ 사용자정의 함수 Return (반환)한 포인터변수(주소값)으로 접근한 메모리 공간

\= 배열 메모리 공간

本 의도한 초기화값 (e.g. 배열 요소 값)

\= 실제 배열 메모리 공간에 초기화된 값 (e.g. 배열 요소 값)

Ref) 큰변수(e.g. 배열, 구조체, 클라스) + 동적 메모리 할당 포인터변수 사용 의의

변수의 크기가 크기 때문에 변수 전체를 사용하기 보다 주소값만으로 접근함이 용이

⇓ In which Case **Static or Dynamic Memory Allocation** is Used

**※ Auto vs Static vs Dynamic Memory Allocation**

| Auto | Dynamic Memory Allocation |
| ---| --- |
| STACK Sector 할당<br>Run Time 시 할당 | HEAP Sector 할당<br>Run Time 시 할당<br> |
| 사용 범위가 지역 변수 (함수 내) | 사용 범위가 지역 변수<br>(함수 내) |
| 사용자정의 함수 종료 후<br>Memory "해제" | 사용자정의 함수 종료 후<br>Memory "유지"<br> |
|  | 많은 Memory 필요한 경우<br><br>일반적인 STACK Sector 용량 (함수 관련 Memory 총량) 제한<br>\= 1MB(= 1000KB)<br>(OS 운영체제 및 PC 마다 상이할 수 있음)<br><br>여유있게 50-100KB보다 큰 Memory<br>\= 동적 할당<br> |
|  | 정확한 Memory 용량을 미리 파악하기 힘든 경우<br><br>알수 없는(e.g. 용량이 증가할 수 있는) 구조(e.g. 배열, 그래프)<br>배열 + Auto 사용<br>Programme 실행중(= Run Time 중 = .exe 파일 실행중)<br>Memory가 할당되기 때문에 배열의 크기를 선언하지 않아도<br>Compiling Error는 발생하지 않지만<br>배열 내부나 외부(Overflow 고려)에 어떤 변수가 작용할지 모르기 때문에 원치않은 Code 실행/결과 도출될 수 있음<br>배열 + Dynamic Memory Allocation 사용<br>Programme 실행중(= Run Time 중 = .exe 파일 실행중)<br>Memory가 "동적으로" 할당<br><br>E.g.) "약" 200명 회원 배열<br>배열 + Auto 사용<br>➝ 배열 크기 선언"하지 않음"<br>➝ 회원수 300명으로 증가<br>➝ Overflow 발생 "가능성" O<br>➝ 원치않은 회원 정보 변경 발생 가능 O<br>Case #2) 배열 + Dynamic Memory Allocation 사용<br>➝ 배열 크기 선언"하지 않아도 됨"<br>➝ 회원"가입" 1명 실행 ➝ Memory 1개 "할당"<br>➝ 회원"탈퇴" 1명 실행 ➝ Memory 1개 "해제"<br>➝ Overflow 발생 X<br>➝ 원치않은 회원 정보 변경 발생 가능 X<br> |
| Memory 누수 없음<br><br>사용자정의 함수 종료<br>\= "자동" Memory "해제" | Memory 누수 발생 가능<br><br>동적 메모리 할당 함수 종료<br>\= 사용자 조취(free 함수 사용) 필요<br>∴ 사용자 조취 누락 = Memory 누수<br> |
| 읽기/쓰기 빠름 | 읽기/쓰기 시간소모 ⭡<br>시간 = 주소값 찾는 과정 + Enque/Deque 과정<br> |

| Static | Dynamic Memory Allocation |
| ---| --- |
| DATA Sector 할당<br>Compile 시 할당 | HEAP Sector 할당<br>Run Time 시 할당 = Programme 실행 중 할당<br> |
| 사용 범위가 지역 변수 (함수 내) | 사용 범위가 지역 변수<br>(함수 내) |
| 사용자정의 함수 종료 후<br>Memory "유지" | 사용자정의 함수 종료 후<br>Memory "유지"<br> |
| "정적" 메모리 할당 | "동적" 메모리 할당 |
| Programme 종료까지<br>무조건 Memory "유지" | Programme 중<br>의도에 따라 Memory "유지" (fee 함수로 "해제" 가능)<br>∴ 한정된 Memory 공간을 효율적/효과적으로 사용 가능<br><br>Programme을 실제로 실행하기 전(Run Time 전)<br>자료의 크기 파악할 수 없는 경우<br>➝ 예상 용량 보다 훨씬 큰 값을 선언 해야할 수 있음<br>배열 + Static<br>Compile시 (.exe 파일 생성시) Hard Disk의 Storage에 할당<br>➝ Programme 실행전 (Run Time 전 = .exe 파일 실행전)에<br>용량 파악 필요<br>배열 + Dynamic Memory Allocation<br>Run Time시 (.exe 파일 실행시) 할당<br>➝ Programme 실행중 (Run Time 중 = .exe 파일 실행중)에<br>용량 파악 필요<br><br>E.g.) "약" 200명 회원 배열<br>배열 + Static 사용<br>➝ 배열 크기 선언 필요 O (약 250개)<br>➝ Memory 할당된 Code Block 시작 ~ Programme 종료<br>까지 Memory 250개 계속 사용<br>➝ 회원수 250명 초과시 "반드시" Overflow 발생 O<br>배열 + Dynamic Memory Allocation 사용<br>➝ 배열 크기 선언 필요 X<br>➝ 회원"가입" 1명 실행 ➝ Memory 1개 "할당"<br>➝ 회원"탈퇴" 1명 실행 ➝ Memory 1개 "해제"<br> |
|  |
| Programme 실행중<br>Run Time 중<br>Memory 크기 변경 X<br>∴ "정적" 메모리 할당<br> | Programme 실행중<br>Run Time 중<br>Memory 크기 변경 O<br>∴ "동적" 메모리 할당<br> |
| Memory 공간 재사용 X<br>∴ "정적" 메모리 할당 | Memory 공간 재사용 O<br>∴ "동적" 메모리 할당<br><br>Static 사용<br>Programme 종료시 까지 "할당"된 Memory 공간 "유지"<br>Dynamic Memory Allocation 사용<br>Programme 중 free 함수로 Memory "해제"후<br>"할당"하여 동일 공간 재사용(다른 용도로도) 가능<br> |
| 사용하기 편리<br><br>Memory 할당된 Code Block 시작 ~ Programme 종료<br>"할당"/"해제" 고정 O<br>∴ "정적" 메모리 할당<br> | 사용하기 불편<br><br>Memory 할당된 Code Block 시작 ~ Programme 종료<br><br><br>"할당"/"해제" 고정 X<br>∴ "동적" 메모리 할당<br> |
| 읽기/쓰기 빠름<br> | 읽기/쓰기 시간소모 ⭡<br>시간 = 주소값 찾는 과정 + Enque/Deque 과정<br> |
| App) Robot Control<br><br>Programme Building 전<br>Robot 설계 완료<br><br>❶ Code<br>Arm 움직임 각도<br>❷ Code<br>Leg 움직임 속도<br><br>❶ Code<br>➝ ❸ Code<br>Motor Control<br>➝ ❹ Code<br>Position Control<br><br>❷ Code<br>➝ ❸ Code<br>Motor Control<br>➝ ❹ Code<br>Position Control<br> | App) 회원 가입 및 관리<br><br>Programme Building 후<br>회원 가입 및 관리 유동적 변동 |
| Wherein Code 실행 전 Fix O | Wherein Code 실행 전<br>Fix X |

**※ Summary #1 - Return Array 배열 반환**

| Return 배열 (➝붕괴➝ 포인터 변수)<br>Return X (➝붕괴➝ &X\[0\]) | 배열(포인터변수) 반환 가능 X<br><br> |
| ---| --- |
| Return Auto 포인터변수 | 포인터변수(주소값) 반환 가능 O<br><br>사용자정의 함수 종료시<br>포인터변수 Memory "해제"<br>➝ 배열 요소 의도값<br>≠ 실제 초기화값<br> |
| ⇓ Solution |
| Return Static 포인터변수<br><br>Return Dynamic Memory Allocation 포인터변수 | 포인터변수(주소값) 반환 가능 O<br><br>사용자정의 함수 종료시<br>포인터변수 Memory "유지"<br>➝ 배열 요소 의도값<br>\= 실제 초기화값<br> |
| ★ 장/단점 비교후 Programme에 맞게 Static or Dynamic Memory Allocation 사용<br>\- Static = "정적" ➝ 사전 정해진 설계<br>\- Dynamic Memory Allocation = "동적" ➝ 유동적 변화 설계 |

**※ Summary #2 - Priority of Auto/Static/Dynamic Memory Allocation in General Use**

*   Priority #1 Auto

가능하면 Auto 변수 사용

∵ 함수 시작 ~ 종료 = 자동 Memory "할당"/"해제"

*   Priority #2 Static vs Dynamic Memory Allocation
장/단점 비교후 Programme에 맞게 Static or Dynamic Memory Allocation 사용
\- Static = "정적" ➝ 사전 정해진 설계
\- Dynamic Memory Allocation = "동적" ➝ 유동전 변화 설계

**③ 함수 포인터변수(주소값) Return 반환**
⇒ CODE(TEXT) Sector "할당" = Complie 시 할당
함수의 주소값 Return (반환)
Assembly Language 기계어가 저장된 함수의 주소값 Return (반환)
E.g.)
"Assembly Language Form 1010101 = Parameter 2개를 더하여 Return 해라"가 "할당"된
함수의 Memory(= RAM의 일정부분을 ROM으로 설정) 주소값 Return (반환)
App)

* * *

②ⓐ Return = Array ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-6378](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-6378))

②ⓑ Return = Dynamic Memory ([https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-6398](https://doc.clickup.com/d/h/8ca07k8-22/5cfed3da07fe658/8ca07k8-6398))