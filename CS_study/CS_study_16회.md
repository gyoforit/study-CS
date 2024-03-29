# CS_study_16회

## 1. [컴퓨터구조] Call by value/address/reference

> actual argument: 전달 인자
>
> formal argument: 매개 변수

함수가 호출될 때 매개변수에 인자를 어떤 방식으로 넣어줄 건지에 대한 세가지 방식입니다.

1. **Call by value**: 값이나 일반 변수를 호출된 함수에 전달하는 것입니다. 전달인자의 값은 매개 변수에 복사됩니다. 따라서 함수의 작동은 전달 인자의 값에 영향을 미치지 않습니다.

   ```c
   void swap(int a, int b)
   {
       int t=a; a=b; b=t;
   }
   int main()
   {
       int a=5, b=10;
       printf("Before swap: a=%d, b=%d", a, b);
       swap(a, b);
       printf("After swap: a=%d, b=%d", a, b);
   }
   ```

   ```
   Before swap: a=5, b=10
   After swap: a=5, b=10
   ```

   main()에서 정의된 변수 a, b는 swap() 함수의 a, b와 변수의 이름은 같지만 주소 값이 다릅니다.

2. **Call by address**: 변수의 주소값을 호출된 함수에 전달하는 것입니다. 전달인자는 매개 변수에 복사되지 않고, 전달 인자의 주소값이 매개 변수에 할당됩니다. 따라서 매개 변수에 대해 함수가 수행하는 작업은 인자 값에 영향을 줍니다.

   ```c
   void swap(int *x, int *y)
   {
       int t=*x; *x=*y; *y=t;
   }
   int main()
   {
       int a=5, b=10;
       printf("Before swap: a=%d, b=%d", a, b);
       swap(&a, &b);
       printf("After swap: a=%d, b=%d", a, b);
   }
   ```

   ```
   Before swap: a=5, b=10
   After swap: a=10, b=5
   ```

   main()에서 정의된 a, b는 swap()의 x, y와 변수의 이름은 다르지만 a와 x, b와 y는 각각 같은 메모리 주소를 가리키고 있습니다.

3. **Call by reference**: 기본 주소값을 호출된 함수에 전달하는 것입니다. 전달인자는 매개 변수에 복사되지 않으며 참조만 됩니다. 따라서 매개 변수에 대해 함수가 수행하는 작업은 인자 값에 영향을 줍니다.

   ```c
   void change(int b[ ])
   {
       b[0]=10; b[1]=20; b[2]=30;
   }
   int main()
   {
       int a[3]={5, 15, 25};
       printf("Before Change: %d, %d, %d", a[0], a[1], a[2]);
       change(a);
       printf("After Change: %d, %d, %d", a[0], a[1], a[2]);
   }
   ```

   ```
   Before Change: 5, 15, 25
   After Change: 10, 20, 30
   ```

   change()에서 정의된 b는 main()의 배열 a를 가리키고 있습니다. 변수의 이름은 다르지만, 둘은 동일한 메모리 주소를 가리키고 있습니다.



## 2.[네트워크] OSI 7계층

국제 표준화 기구(OSI)에서 개발한 모델로 컴퓨터 네트워크 프로토콜 디자인과 통신을 '물리-데이터링크-네트워크-전송-세션-표현-응용'이라는 일곱개의 계층으로 나눈 모델입니다.

1. 물리 계층: 데이터를 전송하기 위한 물리적 전송 매체를 다룹니다.
2. 데이터링크 계층: 데이터 분실, 변형 등 물리적 전송 오류를 감지하는 기능을 제공합니다. 
3. 네트워크 계층: 데이터 전송 시 최적의 경로를 선택할 수 있도록 지원합니다.
4. 전송 계층: 송수신 프로세스 간의 연결 기능을 지원합니다.
5. 세션 계층: 통신하는 시스템 간의 상호작용을 설정, 유지, 동기화합니다.
6. 표현 계층: 압축, 암호화 기능을 통해 표준화된 방법으로 데이터를 인식할 수 있게 합니다.
7. 응용 계층: 사용자의 다양한 네트워크 응용 환경을 지원합니다.



## 3. [운영체제] Process/Thread

1. 프로세스
   - 프로세스는 컴퓨터에서 실행 중인 프로그램을 뜻하며, 운영체제로부터 CPU 시간, 주소 공간, 메모리 등 시스템 자원을 할당 받는 작업의 단위 입니다.
   - 각 프로세스는 최소 한 개의 스레드(메인 스레드)를 가지고 있습니다.
   -  각 프로세스는 별도의 주소 공간에서 실행되기 때문에 다른 프로세스에 접근하기 위해서는 프로세스 간의 통신(IPC, Inter-process communication)이 필요합니다.

2. 스레드
   - 스레드란 프로세스 내에서 실행되는 여러 흐름의 단위로 '경량화된 프로세스'라고도 부릅니다. 프로세스를 별도로 두는 것보다 프로세스 내부에 스레드를 여러개 두는 것이 더 가볍기 때문입니다.
   - 프로세스 내의 스레드는 레지스터와 프로그램 카운터 등 CPU 관련한 것과 스택만 별도로 할당 받으며 코드, 데이터, 힙 영역은 서로 공유합니다. 즉, 같은 프로세스 내 스레드끼리 자원을 공유하기 때문에 한 스레드가 프로세스 자원을 변경하면 다른 스레드가 변경 결과를 즉시 볼 수 있습니다.



## 4. [자료구조] Array/Linked list

> Array와 Linked list의 차이점을 시간 복잡도와 연관지어 설명해주세요.

Array와 Linked list는 데이터를 논리적 순서에 따라 나열한다는 점에서 공통점이 있지만, 물리적 순서에서 차이점이 존재합니다.

1. Array
   - 물리적 순서 또한 순차적입니다.
   - 인덱스를 가지고 있기 때문에 특정 데이터에 접근 시 임의 접근이 가능합니다.
2. Linked list
   - 물리적 순서는 순차적이지 않습니다.
   - 인덱스 대신 이전 데이터의 주소와 다음 데이터의 주소가 저장되어있기 때문에 특정 데이터 접근 시 순차 접근만 가능합니다.
3. 시간복잡도 비교
   1. 데이터 탐색
      - Array: 인덱스를 통한 임의 접근이 가능하기 때문에 O(1)의 시간복잡도를 가집니다.
      - Linked list: 순차 접근 방식을 사용하기 때문에 O(n)의 시간복잡도를 가집니다.
   2. 데이터 추가/삭제
      - Array
        - 맨 처음이나 중간에 데이터 추가/삭제: 뒤의 데이터들을 전부 한 칸씩 뒤로 밀어야 하므로 O(n)의 시간복잡도를 가집니다.
        - 맨 뒤 혹은 배열에 공간 남아있는 경우: O(1)의 시간복잡도를 가집니다.
      - Linked list
        - 데이터를 추가/삭제하는 행위 자체의 시간복잡도는 O(1)입니다.
        - 맨 앞에 데이터 추가/삭제: O(1)의 시간복잡도를 가집니다.
        - 맨 앞 이후에 추가/삭제: 순차적으로 탐색하여 해당 위치까지 가야하므로 O(n)의 시간복잡도를 가집니다.



따라서 데이터의 접근/탐색이 중요하다면 Array를, 추가/삭제가 중요하다면 Linked list를 사용하는 것이 적합할 것 입니다.