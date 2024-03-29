# CS_study_23회

## 1. [알고리즘] Python sort()

> Python의 내장함수 sort에 사용된 정렬 방식을 설명해주세요.

- Python의 sort() 함수에 쓰인 알고리즘은 Timsort입니다.
- 삽입 정렬과 병합 정렬을 섞은 알고리즘으로, 정렬을 해야하는 전체 덩어리를 작은 덩어리로 자른 후 각각의 덩어리를 삽입 정렬로 정렬한 뒤, 병합 정렬로 병합하는 정렬입니다.

- '실제 데이터는 대부분 이미 정렬되어있을 것이다'라는 가정에 기반한 정렬 알고리즘으로 평균 O(nlogn)의 시간 복잡도를 가지며 stable sort에 속합니다.
- Python뿐만 아니라 Java SE 7, Android, Google chrome (V8), Swift 등에서 표준 정렬 알고리즘으로 채택된 알고리즘입니다.



## 2. [자료구조] B+tree

- B+tree 구조는 B-tree와 구조가 유사하지만, 리프노드가 연결리스트의 형태를 띠어 선형 검색이 가능하다는 점에서 차이가 있습니다. 이러한 특징으로 인해 신속한 검색이 가능합니다.

![img](https://media.vlpt.us/images/emplam27/post/64290106-d927-4a82-9e08-8e52783c7dd3/DB%20%EC%9D%B8%EB%8D%B1%EC%8A%A4.jpg)

![img](https://media.vlpt.us/images/emplam27/post/bcbce100-d475-4cda-aebe-946d1813949c/B%ED%94%8C%EB%9F%AC%EC%8A%A4%20%ED%8A%B8%EB%A6%AC%20%EA%B8%B0%EB%B3%B8%20%ED%98%95%ED%83%9C.jpg)

- B+tree의 특징
  1. 모든 key, data가 리프노드에 모여있습니다.
     - B-tree는 리프노드가 아닌 각 key마다 data를 가진다는 점에서 차이가 있습니다.
  2. 모든 리프노드가 연결리스트의 형태를 띠고 있습니다.
     - B-tree는 옆 리프노드를 검사 시 다시 루프노드부터 검사해야 하지만 B+tree는 리프노드에서 선형검사를 수행할 수 있어 시간복잡도가 크게 줄어듭니다.

참고: https://velog.io/@emplam27/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%EA%B7%B8%EB%A6%BC%EC%9C%BC%EB%A1%9C-%EC%95%8C%EC%95%84%EB%B3%B4%EB%8A%94-B-Plus-Tree



## 3. [운영체제] CISC / RISC

CISC, RISC는 CPU를 설계하는 방식입니다. CPU가 작동하려면 프로그램이 있어야 하고, 명령어를 주입해서 설계를 하는데 명령어가 S/W 적인 방식을 CISC, H/W적인 방식을 RISC라고 합니다.

### 1. CISC (Complex Instructon Set Computer)

- 복잡하고 많은 종류의 명령어와 주소 지정 모드를 사용합니다.
- 가변 길이 명령어 형식입니다.
- 100~250개 정도의 많은 명령어를 가지고 있어 설계가 어렵습니다.
- 명령어가 S/W적이므로 호환성이 좋습니다.
- 명령어를 해석한 후 명령어를 실행합니다.
- 컴파일이 쉽고 호환성이 좋은 장점이 있지만 속도가 느립니다.
- Intel 사의 CPU에 주로 사용됩니다.

### 2. RISC (Reduced Instruction Set Computer)

- 간단하고 적은 종류의 명령어와 주소 지정 모드를 사용합니다.
- 고정 길이 명령어 형식이므로 해석 속도가 빠릅니다.
- CISC에 비해 명령어 수가 적습니다.
- CISC에 비해 설계 구조가 상대적으로 간단합니다.
- 논리 회로를 이용한 하드웨어적 제어 방식입니다.
- 효율성이 떨어지고 전력 소모가 적지만, 처리 비트 단위가 변하거나 프로세서 구조가 조금만 바뀌어도 하위 프로세서와의 호환성이 떨어집니다.
- 고성능의 워크스테이션과 그래픽용 컴퓨터에서 주로 사용됩니다.



## 4. [네트워크] 로드밸런싱

### 1. 개념

로드 밸런싱이란 서버에 접속하는 클라이언트가 증가했을 때, 서버에 가해지는 부하를 분산해주는 장치 또는 기술을 의미합니다. 클라이언트-서버 사이에 위치하여 특정 서버로 부하가 집중되지 않도록 트래픽을 관리합니다. 서버 과부하로 인해 서비스가 작동하지 않는 것은 심각한 문제가 될 수 있으므로 서비스 이용자 수가 많은 시스템에서는 반드시 사용해야 합니다.



### 2. 로드 밸런싱 알고리즘

1. 라운드 로빈 방식: 서버에 들어온 요청을 순차적으로 배정합니다.
2. 가중 라운드 로빈 방식: 각각의 서버마다 가중치를 매기고, 가중치 높은 서버에 우선적으로 배정합니다. 각 서버의 트래픽 처리 속도가 상이한 경우 적합합니다.
3. IP 해시 방식: 클라이언트의 IP 주소를 해시 함수를 통해 특정 서버에 매핑합니다.
4. 최초 연결 방식: 요청이 들어온 시점에 가장 적은 연결 상태를 보이는 서버에 우선적으로 배정합니다.



### 3. 로드 밸런서 종류

- OSI 7계층에 따라 L1부터 L7까지 존재하지만, 가장 많이 활용되는 것은 L4, L7 입니다.

1. L4 로드 밸런서
   - 네트워크 계층(IP), 전송 계층(TCP, UCP)의 정보를 바탕으로 로드를 분산합니다.
   - 장점
     1. 데이터를 확인하지 않고 패킷 레벨에서 로드를 분산하기 때문에 빠르고 효율적입니다.
     2. 데이터를 복호화할 필요가 없으므로 안전합니다.
     3. 가격이 저렴합니다.
   - 단점
     1. 섬세한 라우팅이 불가합니다.
     2. 사용자의 IP가 수시로 바뀌는 경우 연속적인 서비스를 제공할 수 없습니다.
2. L7 로드 밸런서
   - 응용 계층(HTTP, FTP, SMTP)에서 로드를 분산합니다.
   - HTTP 헤더, 쿠키 등 사용자 요청을 기준으로 특정 서버에 트래픽을 분산할 수 있습니다. 즉, 패킷의 내용을 확인한 후 그 내용에 따라 로드 밸런싱을 진행합니다.
   - 장점
     1. 클라이언트의 요청을 세분화하여 서버에 전달할 수 있습니다.
     2. 캐싱 기능을 제공합니다.
     3. DOS같은 비정상적 트래픽을 필터링할 수 있어 안정성이 높습니다.
   - 단점
     1. 패킷 내용을 복호화해야 하므로 비용이 많이 듭니다.
     2. 클라이언트와 로드밸런서가 인증서를 공유해야하기 때문에 보안상의 위험이 있습니다.