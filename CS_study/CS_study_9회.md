# CS_study_9회

## 1. [자료구조] 해시테이블

> 해시테이블에 대해 간단히 설명해주세요.

해시테이블은 (key, value) 구조로 자료를 저장하며, key값에 해시함수를 적용하여 고유한 index를 형성(index가 저장되는 장소=버킷)하고, 이를 활용하여 값을 저장/검색하는 자료구조 입니다. 이러한 구조로 데이터를 저장하면 key값으로 데이터를 찾을 때 해시함수를 한번만 수행하면 되기 때문에 해시테이블의 평균 시간복잡도는 O(1) 입니다.

Java에서 해시테이블과 비슷한 자료구조로 해시맵이 있습니다. 해시맵과 해시테이블의 차이는 동기화 지원 여부입니다. 해시맵의 경우 병렬처리, 자원의 동기화를 지원하지 않지만 해시테이블의 경우 병렬 프로그래밍과 자원의 동기화가 가능합니다.



(학습을 위한 추가적인 내용)

- 해시값의 충돌: 해시테이블의 서로 다른 key가 같은 index를 가지고 있을 때 (이 경우 O(N)까지 시간복잡도 증가)
- 해결법: 분리 연결법, 개방 주소법
  - 분리 연결법: 동일한 index의 데이터에 대해 추가적인 메모리를 사용하여 다음 데이터의 주소를 저장
    - 장점: 간단한 구현이 가능
    - 단점: 데이터의 수가 많아지면 그만큼 메모리 차지
  - 개방 주소법: 비어있는 해시 테이블의 공간을 활용하는 방법
    - 유형 1: Linear Probing - 현재의 index로부터 고정폭만큼 이동하여 차례대로 검색 -> 비어있는 버킷에 데이터 저장
    - 유형 2: Quadratic Probing - 해시의 저장순서 폭을 제곱으로 저장하는 방식. 처음 충돌 발생 시 1만큼 이동, 그 다음 부터는 2^2, 3^2
    - 유형 3: Double Hashing Probing - 해시된 값을 한 번 더 해싱하여 해시의 규칙성을 없애버림
    - 장점: 추가적인 메모리를 사용하지 않음
    - 단점: 빈 공간을 활용하기 때문에 해시테이블 재정리 필요



## 2. [운영체제] 교착상태

> 교착 상태(Deadlock)의 4가지 조건에 대해 알고있나요?

교착 상태는 일련의 프로세스들이 CPU, memory space 등의 자원을 기다리며 block된 상태를 뜻합니다. 

이러한 교착 상태가 발생되는 네 가지 조건은 상호 배제, 비선점, 보유대기, 순환대기가 있습니다.

상호 배제는 매 순간 하나의 프로세스만이 자원을 사용할 수 있음을 뜻합니다. 만약 여러 프로세스가 자원을 동시에 사용할 수 있다면 자원을 기다리는 일이 없을 것입니다.

비선점이란 프로세스는 자원을 스스로 내어놓을 뿐, 강제로 빼앗기지 않음을 뜻합니다. 선점형 스케줄링처럼 우선순위에 따라 자원을 선점하게 된다면 교착상태가 생기지 않을 것입니다.

보유대기란 자원을 가진 프로세스가 다른 자원을 기다릴 때 보유 자원을 포기하지 않고 계속 가지고 있음을 뜻합니다. 만약 자원을 사용 시 전부 사용하는 것이 아니면 전부 포기하게 만든다면 교착상태가 생기지 않습니다.

순환대기란 자원을 기다리는 프로세스 간 싸이클이 형성되어야 합니다. 가령 프로세스1이 프로세스2의 자원을 기다리고, 프로세스2가 3의 자원을, 3이 1의 자원을 기다린다면 싸이클이 형성되고 교착상태가 일어날 것입니다.



## 3. [알고리즘] Quicksort

> Quicksort의 과정에 대해 간단히 설명해주세요.

퀵 소트의 과정을 한 문장으로 요약한다면 '피벗(pivot)이 자신의 자리를 찾아가며 정렬되는 과정' 이라고 할 수 있습니다. 

퀵 소트를 진행하기 위해 우선 가장 처음/중간/마지막 수 중 하나를 첫번째 피벗으로 선택합니다. 그 후 양 끝의 인덱스를 각각 i, j라고 정합니다. i는 오른쪽으로 이동하며 피벗보다 큰 수를 찾고, j는 왼쪽으로 이동하며 피벗보다 작은 수를 찾아 i와 j 요소를 서로 교환함으로써 피벗을 기준으로 왼쪽에 피벗보다 작은 수, 오른쪽에 피벗보다 큰 수를 배치하게 합니다. 이 후 양 쪽을 각각 퀵정렬 하는 분할정복의 방법을 사용하여 정렬을 완료하게 됩니다.

이러한 퀵정렬의 시간복잡도는 평균적으로 O(nlogn)이나, 최악의 경우 O(n^2)가 됩니다. 이는 수가 역순으로 정렬되어있을 때 피벗을 가장 첫번째 수로 선택하는 경우입니다. 따라서 피벗을 중간 수로 선택한다면 최악의 시간복잡도를 피할 수 있습니다.



## 4. [개발상식] 애자일방법론

> 애자일 방법론의 개념과 이를 적용한 본인의 프로젝트가 있다면 간단히 설명해주세요.

애자일 방법론이란 변화에 빠르게 대응하기 위해 등장한 소프트웨어 개발 방법론입니다. 절차보다 사람을 중시하며 개발기간이 짧고 신속하다는 특징이 있습니다.

애자일 방법론 중 스크럼 유형을 적용하여 프로젝트를 진행했습니다. 영화 커뮤니티 서비스를 구축하는 프로젝트였는데, 당시 개발 기간이 약 일주일 정도로 굉장히 짧았습니다. 따라서 빠른 이슈 대응이 필요하다고 생각하여 매일 주 2회 스크럼 미팅을 진행하며 팀원들의 진행 상황과 발생한 이슈들을 파악했습니다. 또한 'Trello'라는 툴을 사용하여 이슈들을 칸반보드에 기록하여 프로젝트를 관리했습니다.
