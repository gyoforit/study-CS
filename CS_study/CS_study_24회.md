# CS_study_24회

## 1. [자료구조] Trie

![image-20211108181113485](C:\Users\gyoforit\AppData\Roaming\Typora\typora-user-images\image-20211108181113485.png)

### 1. 개념

- 트라이는 문자열을 저장하고 효율적으로 탐색하기 위한 트리형태의 자료구조 입니다.

- 검색 시 자동완성 기능이나 사전 검색 등 문자열 탐색에 특화되어 있습니다.

- 트라이의 한 노드를 표현하는 객체는 자손 노드들을 가리키는 포인터 목록과 이 노드가 종료 노드인지를 나타내는 boolean 변수로 구성됩니다.

### 2. 장단점

- 장점

    - 루트에서 한 노드까지 내려가는 경로에서 만나는 글자들을 모으면 해당 노드에 대응되는 접두사를 얻을 수 있습니다. 따라서 각 노드에 대응되는 문자열을 따로 저장할 필요가 없습니다.

    - 예를 들어 hello에서 hell과 hello는 하나의 경로에 함께 저장합니다.


-  단점

  - 포인터 배열로 인해 필요로 하는 공간이 너무 크다는 문제입니다. 알파벳 대문자만 저장해도 트라이의 각 노드는 26개의 포인터를 저장해야 합니다.
  - 입력되는 문자열들이 접두사를 전혀 공유하지 않는 최악의 경우 트라이에는 입력되는 문자열들의 전체 길이만큼의 노드가 필요합니다.

### 3. 시간복잡도

- 생성 시간 복잡도: O(M*L) (M: 총 문자열들의 수, L: 제일 긴 문자열의 길이)
  - 모든 문자열 M개를 넣어야 하고 M개에 대해 트라이에 넣는 것은 가장 긴 문자열 길이인 L만큼 걸리기 때문입니다.
- 탐색 시간 복잡도: O(L)
  - 트리를 제일 깊게 탐색하는 경우는 가장 긴 문자열 길이인 L까지이기 때문입니다.



## 2. [운영체제] Synchronous / Blocking

> 동기와 비동기, 블로킹과 논블로킹에 대해 설명해주세요.

### 1. 동기/비동기

- 동기/비동기는 호출되는 함수의 작업 완료 여부를 누가 신경 쓰는지에서 차이점이 존재합니다.
- 동기: 호출하는 함수가 호출된 함수의 작업 완료 여부를 스스로 확인하는 방식입니다.

- 비동기: 호출하는 함수가 호출되는 함수에게 callback을 넘기기 때문에 호출하는 함수는 호출된 함수의 작업 완료 여부를 신경쓰지 않고 호출된 함수에서 작업을 완료한 후 callback 함수를 실행하는 방식입니다.



### 2. 블로킹/논블로킹

- 블로킹/논블로킹은 호출되는 함수가 제어권을 호출한 함수로 넘겨주는지에서 차이점이 존재합니다.
- 블로킹: 호출된 함수가 자신의 작업을 모두 완료할 때까지 호출한 함수에게 제어권을 넘겨주지 않는 방식입니다.
- 논블로킹: 호출된 함수가 바로 호출한 함수에게 제어권을 넘겨주고, 호출한 함수가 다른 일을 할 수 있도록 하는 방식입니다.



### 3. 네 가지 유형

|          | 동기                                                         | 비동기                                                       |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 블로킹   | ![](https://blog.kakaocdn.net/dn/dEcl2Q/btq2NEHwYCo/2mSRldzX8KPF4ew65Q7u11/img.png)작업이 완료될 때까지 호출한 함수는 대기하며(동기), 수행 완료 여부는 호출된 함수에서 관리합니다(블로킹). | ![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FmooW7%2Fbtq2McyK8UJ%2FoxQisQ5sKWkVA878XLCs6K%2Fimg.png)호출된 함수에서 모든 작업을 수행하면 callback 함수를 호출하며(비동기), 제어권을 호출된 함수에서 가지기 때문에 호출한 함수는 다른 작업을 할 수 없습니다(블로킹). |
| 논블로킹 | ![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fbdm4V4%2Fbtq2My2pWXl%2FP26PSckFMrSOXAuAtrBCO1%2Fimg.png)호출된 함수는 호출한 함수에게 바로 제어권을 넘겨주며(논블로킹), 호출한 함수는 다른 작업을 하다가 호출된 함수에서 작업 완료 여부를 수시로 확인합니다(동기). | ![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbAJlbP%2Fbtq2NpjzES9%2FfR5XMOxutFtgHwV5Kus1AK%2Fimg.png) 호출된 함수는 호출한 함수에게 바로 제어권을 넘겨주며(논블로킹), 호출된 함수에서 작업이 완료되면 callback 함수를 호출하여 수행을 완료합니다(비동기). |



## 3. [네트워크] IP주소 / MAC주소

### 1. IP주소

- IP주소는 인터넷에 연결된 장치를 식별하는 고유한 번호의 집합입니다. 논리 주소라고 할 수 있습니다.
- 네트워크 계층에서 사용합니다.
- 인터넷 작동 방식
  - 인터넷은 서로 연결된 별도의 네트워크로 구성되며, 각 네트워크를 인터넷 서비스 공급자(ISP)라고 합니다. 
  - ISP에서 서비스를 구입하면 해당 ISP의 네트워크에 연결할 수 있으며, 해당 ISP에 연결된 다른 네트워크에 접근할 수 있습니다.
  - 모든 ISP에는 관리하는 IP주소 풀이 있으며 서비스를 구매하면 IP주소가 할당됩니다.
  - 인터넷의 데이터가 사용자에게 도달해야 할 때 ISP의 네트워크는 사용자의 고유 IP 주소가 대상임을 확인한 후, 해당 데이터를 사용자에게 라우팅 합니다.
- IP주소 종류
  - IPv4: 마침표로 구분된 4개의 숫자 세트처럼 보이는 형태. 각 숫자는 0에서 255 사이에 있습니다.
  - IPv6: 콜론으로 구분된 8개의 4자 문자열 세트처럼 보이는 형태. 각 문자열에는 숫자와 소문자가 포함됩니다.

### 2. MAC주소

- MAC(Media Access Control) 주소는 장치에서 고유한 네트워크 인터페이스를 식별합니다. IP주소는 ISP에 의해 할당되고 장치가 연결 및 해제될 때 다시 할당될 수 있지만, MAC 주소는 물리적 어댑터에 연결되고 제조업체에서 할당합니다. 즉, 물리 주소라고 할 수 있습니다.

- 데이터 링크 계층에서 사용합니다.

- MAC 주소는 12자리 문자열로서 각 숫자는 0에서 9까지의 숫자 또는 A와 F 사이의 문자로 이루어져 있습니다. 세 가지 일반적인 형식이 있습니다.

  1. 61 : 4A : 34 : 1F : 43 : 70 (가장 일반적인 형식)
  2. 61-4A-34-1F-43-70
  3. 614.A34.1F4.370

  - 처음 여섯자리는 어댑터 제조 번호 업체, 마지막 여섯자리는 해당 어댑터의 고유 식별 번호입니다.

- MAC 주소의 중요성

  - 라우터에서 MAC주소를 이용하여 필터링 할 수 있습니다.
    - 특정 MAC주소에 대한 접근을 거부하거나 특정 MAC주소만 연결되도록 라우터에 지시할 수 있습니다.



## 4. [알고리즘] LRU 알고리즘

- 개념: 페이지 교체 알고리즘 중 하나로 페이지 부재 발생시 가장 오랫동안 사용되지 않은 페이지를 제거하는 알고리즘입니다.

- 구현

  ```python
  cache_size = 5
  page_list = ['a', 'b', 'c', 'b', 'c', 'd', 'b', 'e', 'a']
  cache = []
  
  for page in page_list:
      # 찾는 페이지가 있다면 해당 페이지를 최근으로 변경
      if page in cache:
          cache.remove(page)
          cache.insert(len(page_list-1), page)
      # 없다면 가장 오래된 요소 삭제 후 해당 페이지 삽입
      else:
          if len(cache) >= cache_size:
              cache.pop(0)
          cache.append(company)
  ```

  

  
