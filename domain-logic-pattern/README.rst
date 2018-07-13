Domain Logic Pattern
--------------------

여기에서 도메인 로직 구성은 크게 3가지로 나누어서 진행할 예정인다.
각각은 아래와 같다.
::

  1) Transaction Script
  2) Domain Model
  3) Table Module


Transaction Script
------------------

트랜잭션 스크립트 패턴은 아래와 같은 구조를 갖게 된다. 


  | Input(from Presentation Layer) -> Validation & Calulation(Domain Layer) -> Store Data(Data Source Layer) or Invoke Other system


장점
::

  1) 대부분 개발자가 이해하는 간단한 프로시져 모델 형태로 됨
  2) Row Data Gateway or Table Data Gateway와 연동되는 간단한 모델이 생성가능함
  3) 트랜잭션 바운더리를 지정하기 쉬움


단점
::

  1) 도메인 복잡성이 높아질 수록 복잡도가 증가함
  2) 공통적인 서브루틴의 개념으로 중복되는 부분을 줄이고 잇지만 중복되는 소스를 제거하는 것이 쉽지 않음
  3) 분명한 구조 없이는 얽키고 설킨 구조가 되기 쉬움


| 복잡도가 높은 도메인 로직은 Domain Model을 사용해야 하는데, 이를 위해서는 oop로 개념전환이 필요함


