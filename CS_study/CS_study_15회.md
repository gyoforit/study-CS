# CS_study_15회

## 1. [알고리즘] stable / unstable sort

> stable sort와 unstable sort가 무엇인지 예시와 함께 설명하고, 어떤 알고리즘이 있는지 분류해주세요.

정렬이 stable 하다는 것은 '중복된 값들의 순서가 정렬 후에도 그대로 유지된다'는 뜻입니다.

예를 들어 `[9, 4, 7, 2, 7, 1]` 이라는 리스트에서 중복되는 7을 앞에서부터 `7(1), 7(2)` 라고 가정해보겠습니다. 이 때, 정렬 후 `[1, 2, 4, 7(1), 7(2), 9]` 처럼 중복된 값의 순서가 그대로 유지된다면 stable한 정렬이며 순서가 유지되지 않는다면 unstable한 정렬이라고 합니다.

이러한 Stable sort의 대표적인 정렬 알고리즘은 삽입 정렬, 병합 정렬, 버블 정렬, 카운팅 정렬이 있습니다.

1. 삽입 정렬
   - 자신보다 큰 값들에 대해서만 index를 하나씩 증가시켜 insert를 하는 정렬이므로 중복된 값들의 순서가 변하지 않습니다.
2. 병합 정렬
   - 두 그룹을 병합할 때, 같은 값이 나온다면 앞의 그룹 숫자를 먼저 갖다 써야 stability가 훼손되지 않습니다.
3. 카운팅 정렬
   - 오른쪽에서 왼쪽으로 요소들을 훑으면서 해당 요소의 개수를 저장한 Counting Array의 인덱스 값에 따라 오른쪽에서 왼쪽으로 수를 재배열하기 때문에 stability가 훼손되지 않습니다.



한편 Unstable sort의 대표적인 정렬 알고리즘은 퀵 정렬이 있습니다.

예를들어 `[3, 5(1), 5(2)]` 리스트를 퀵 정렬할 때, pivot을 맨 마지막 `5(2)`로 정했다고 가정해보겠습니다. 이 때 pivot 기준 작은 구간은 `3`, 큰 구간은 `5(1)`이 됩니다. 따라서 `5(2)`를 큰 구간의 첫번째 값 `5(1)`과 교환하여 `[3, 5(2), 5(1)]`이 되기 때문에 불안정 정렬이라고 할 수 있습니다.



## 2. [자료구조] 해시테이블

> 해시테이블을 구현하는 방법에 대해 설명해주세요.

![01](https://hudi.blog/static/84dbfefa80d314b753af2d8176974517/ca1dc/01.png)

해시테이블은 key와 value를 기반으로 데이터를 저장하는 자료구조입니다.

key가 해시함수를 거치면 hash가 되고, 이 hash를 배열인 buckets의 key로 삼아 value를 저장합니다. 따라서 데이터를 서칭하는 과정에서 배열을 순차적으로 탐색할 필요 없이 해시 함수를 거쳐 생성된 해시 값으로 데이터를 빠르게 찾을 수 있습니다.

해시테이블을 구현하는 방법에는 해시 충돌 대응에 따라 두가지로 나뉩니다. 해시 충돌이란 서로 다른 key의 hash 값이 중복되어 나타나는 충돌입니다. 즉, 서로 다른 두 key를 hash로 변환했을 때 무조건 다른 해시 값이 도출되는 것을 보장하지 않는 것입니다. 

1. Chaining
   - 각 bucket에 대응하는 linked list를 생성하고 bucket이 linked list의 가장 앞 노드를 바라보게 하여 충돌을 방지하는 방법입니다. 해시 충돌이 발생했을 때 해당하는 해시의 linked list 마지막 노드로 추가합니다. 이를 '열린 해시법'이라고도 부릅니다.
2. Open addressing
   - Chaining 방법과 달리 한 bucket에는 하나의 value만 저장하며, 해시 충돌 시 key를 재해싱하는 방법입니다. '닫힌 해시법'이라고도 부릅니다. Python의 dictionary 구조가 해당 방식을 채택했다고 합니다.



## 3. [운영체제] 교착상태(Deadlock)

> 교착상태의 4가지 조건에 대해 말씀해주세요.

교착상태란 두 개 이상의 작업이 서로가 끝나기를 기다리는 채로 무한히 대기하는 상황을 뜻합니다. 이러한 교착 상태가 발생되는 네 가지 조건으로는

1. 상호 배제 (Mutual exclusion)
   - 매 순간 하나의 프로세스만이 자원을 사용할 수 있다는 것입니다.
   - 만약 여러 프로세스가 자원을 동시에 사용할 수 있다면 자원을 기다리는 일이 없을 것입니다.
2. 비선점 (No preemption)
   - 프로세스는 자원을 스스로 내어놓을뿐 강제로 빼앗기지 않는다는 것입니다.
   - 선점형 스케줄링처럼 우선순위에 따라 자원을 선점하게 된다면 교착상태가 생기지 않을 것입니다.
3. 점유 대기 (Hold and wait or resource holding)
   - 자원을 가진 프로세스가 다른 자원을 기다릴 때 하나 이상의 자원을 점유하고 있는 것입니다.
   - 만약 자원을 사용할 때, 전부 사용하는 것이 아니라면 전부 포기하게 만든다면 교착상태가 생기지 않습니다.
4. 순환 대기 (Circular wait)
   - 자원을 기다리는 프로세스 간 싸이클이 형성되어야 합니다.
   - 프로세스1이 프로세스2의 자원을, 프로세스2가 프로세스3의 자원을, 프로세스3이 프로세스1의 자원을 기다린다면 싸이클이 형성되어 교착상태가 일어날 것입니다.



## 4. [네트워크] TCP/UDP

> TCP와 UDP에 대해 자세히 설명해주세요.

우선 TCP와 UDP의 공통점은 OSI 표준모델과 TCP/IP 모델의 전송계층에서 사용되는 프로토콜이라는 것입니다. 즉, 데이터의 전달을 담당하는 프로토콜입니다. 따라서 포트 번호를 이용하여 주소를 지정한다는 점, 데이터 오류 검사를 위한 체크섬이 존재한다는 점에서 추가적인 공통점을 갖습니다.

1. TCP (Transmission Control Protocol)

   ![img](https://blog.kakaocdn.net/dn/IVBAk/btqNlmuFIm3/je46XorKIeFVz93PbkxODk/img.png)

   - 특징

     - 연결 지향적 프로토콜입니다. 클라이언트와 서버가 연결된 상태에서만 데이터를 주고받을 수 있습니다.

       - 클라이언트가 연결 요청(SYN)을 하고 서버가 연결을 수락하면 통신 선로가 고정되고, 모든 데이터는 이 고정된 통신 선로를 통해 순차적으로 전달됩니다. 따라서 TCP는 데이터를 정확하고 안정적으로 전달할 수 있습니다.
       - 이러한 연결 절차로 인해 상대적으로 UDP에 비해 속도가 느리다는 단점이 있습니다.

     - 신뢰성 있는 데이터를 전송합니다.

       - TCP는 패킷을 성공적으로 전송하면 ACK 라는 신호를 날리고, 만약 ACK 신호가 제 시간에 도착하지 않으면 TImeout이 발생하여 손실이 발생한 패킷을 다시 전송해줍니다. 이렇듯 데이터 통신마다 확인 응답을 주고받는 절차가 있어 통신의 신뢰성이 올라갑니다.

     - 데이터의 전송 순서를 보장합니다. 데이터의 순서 유지를 위해 각 바이트마다 번호를 부여하기 때문입니다.

     - 참고: 3 way handshake 방식

       ![img](https://blog.kakaocdn.net/dn/c7IA52/btqNfrrcasU/B0UyfjyjKh1Ga6yQB3v2y0/img.jpg)

       1. 클라이언트에서 서버에 연결 요청하기 위해 SYN 데이터 전송
       2. 서버에서 해당 포트는 LISTEN 상태에서 SYN 데이터 받고 SYN_RCV로 상태 변경
       3. 서버는 요청을 정상적으로 받았다는 뜻인 ACK와 클라이언트 포트 열어달라는 SYN 함께 전송
       4. 클라이언트에서는 SYN+ACK 받고 ESTABLISHED 상태로 변경 후 서버에 ACK 전송
       5. ACK를 받은 서버는 ESTABLISHED로 상태 변경

   

2. UDP (User Datagram Protocol)

   ![img](https://blog.kakaocdn.net/dn/db4ChG/btqNkfv2W6U/RPlPzrfgr0YbZUa7XLcrw1/img.png)

   - 특징
     - 비연결 지향적 프로토콜입니다. 데이터를 주고 받을 때 연결 절차를 거치지 않고 발신자가 일방적으로 데이터를 발신하는 방식입니다. 따라서 상대적으로 TCP에 비해 전송 속도가 빠릅니다.
     - TCP와 달리 패킷이 중간에 유실, 변조되어도 재전송을 하지 않습니다. 따라서 데이터 전달의 신뢰성이 떨어집니다.
     - 데이터의 전송 순서를 보장하지 않습니다. 발신자가 데이터 패킷을 순차적으로 보내더라도 이 패킷들은 서로 다른 통신 선로를 통해 전달되기 때문입니다.