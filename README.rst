Enterprise Architecture
-----------------------
  |  해당 자료는 마틴 파울러의 책을 정리한 것이며 큰 그림으로 부터 상세한 내용을 정리하기 위하여 만들었다. 
  |  아키텍처는 성능적인면과 확장성적인 면을 고려하여 시스템에서 상위에서 디자인하고 구현하는 것이다. 
  |  이 책에서는 아키텍처는 반쪽만 구워진 빵이라고 하듯 아키텍처는 적용되고 약간의 수정과 조정을 거친후 오전하게 만들어진다. 
  |  빵을 만들러 오늘도 즐거운 한발짝을 걸어보자.


Layered Architecture
--------------------
  |  이 책에서는 다양한 패턴보다는 기업에서 많이 쓰이는 'Layered Architecture'를 기본으로 디자인하는 것을 가정하고 있다.
  |  그래서 이책에서 만들하는 Layered Architecture의 큰 그림을 먼저 살펴보도록 하자.


Layering
--------
  | 'Layering'은 복잡한 시스템을 분리할때 사용하는 일반적인 패턴으로 유용하다.
  | 레이어 형태의 디자인을 생각할때 다음과 같은 특징이 있을 것이다

  1) 상위 레이버는 하위 레이어를 의존한다.
  2) 하위 레이버는 상위 레이어에 대하여 모른다.
  3) 단점으로 상위레이어이 변화가 하위레이어들에 영향을 줄 수 있음(Cascading changes)


* 해당 책에서는 레이어를 3개로 분리해서 설명한다. 세 개의 레이어의 일반적인 내용을 먼저 확인해 보자.

  +--------------------+
  |     Presentation   | 
  +--------------------+
  |    Domain Logic    |
  +--------------------+
  |      Data Source   | 
  +--------------------+

  .. code-block:: text
  
    Presentation: User and S/W와 어떻게 상호작용할지르 책임지는 레이어
    Dmomain Logic: 비지니스 로직이라고도 불리며 도메인에서 실제 다루어야 하는 로직을 뜻하며 저장된 데이터와 주어진 데이터를 기반으로 계산 및 검증을 담당
    Data Source: 다른 시스템과 통신을 담당하는 역할, 기업아키텍처에서는 저장해야 하는 데이터를 대부분으로 이루어짐


Patterns
----------
각 레이어 별로 속하는 패턴이 다르게 존재할 것이다. 이때, 개별 레이어마다 특징적인 문제들이 존재할 것이다. 
이를 해결하기 위한 것이 아래에 나와 있는 것과 같이 패턴으로 설명된다.
먼저 아래 해당 패턴들이 의미하는 바를 살펴보고 가령 왜 패턴이 생겼으며 어떤 문제를 해결하기 위함인지 확인해 보고, 개별적인 내용을 쫓아가 보도록 하겠다.\

  | `Domain Logic Patterns`_: Transaction Script (110), Domain Model (116), Table Module (125), Service Layer (133).
  |
  | Data Source Architectural Patterns: Table Data Gateway (144), Row Data Gateway (152), Active Record (160), Data Mapper (165).
  |
  | Object-Relational Behavioral Patterns: Unit of Work (184), Identity Map (195), Lazy Load (200)
  |
  | Object-Relational Structural Patterns: Identity Field (216), Foreign Key Mapping (236), Association Table Mapping (248), Dependent Mapping (262), Embedded Value (268), Serialized LOB (272), Single Table Inheritance (278), Class Table Inheritance (285), Concrete Table Inheritance (293), Inheritance Mappers (302).
  |
  | Object-Relational Metadata Mapping Patterns: Metadata Mapping (306), Query Object (316), Repository (322).
  |
  | Web Presentation Patterns: Model View Controller (330), Page Controller (333), Front Controller (344), Template View (350), Transform View (361), Two-Step View (365), Application Controller (379).
  |
  | Distribution Patterns: Remote Facade (388), Data Transfer Object (401)
  |
  | Offline Concurrency Patterns: Optimistic Offline Lock (416), Pessimistic Offline Lock (426), Coarse Grained Lock (438), Implicit Lock (449).
  |
  | Session State Patterns: Client Session State (456), Server Session State (458), Database Session State (462).
  |
  | Base Patterns: Gateway (466), Mapper (473), Layer Supertype (475), Separated Interface (476), Registry (480), Value Object (486), Money (488), Special Case (496), Plugin (499), Service Stub (504), Record Set (508)

Reference
---------
.. _`Domain Logic Patterns`: ./domain-logic-pattern/README.rst


Copyright & License
--------------------