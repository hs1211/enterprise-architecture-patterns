Data Source Architectural Patterns
----------------------------------
이 패턴들은  data source layer를 패턴으로 정리해 놓은 것으로 데이터베이스와 통신하는 것을 주 역할로 하고 있다.


Gateway Patterns
----------------

SQL 액세스를 도메인 로직과 분리하는 것은 현명한 방법이다. 이런 방법 중 하나로 데이터 베이스 테이블 하나가 클래스가 되도록 생성하는 방식을 "Gateway"라고 한다.
아래에서는 2개의 게이트웨이 방식을 소개하겠다.

::

  1.Row Data Gateway
    이 방식은 테이블의 한 행을 객체로 생성하는 방식으로 Row : Class = 1 : 1의 관계를 갖는다.

    e.g)
        +----------------+
        | Person Gateway |
        +----------------+
        |    lastname    |
        |    firstname   |
        +----------------+
        |    find(id)    |
        +----------------+

  2.Table Data Gateway
    이 방식은 Record Set와 같이 사용하는 방식으로 Table : Class = 1: 1의 관계를 갖는다.
    아래 RecordSet 자체의 인터페이스를 통하여 테이블 접근이 가능한 형태가 된다.

    e.g)
        +-------------------------+
        |       Person Gateway    |  
        +-------------------------+
        | find (id) : RecordSet   |
        +-------------------------+


Understading RecordSet
----------------------
Record Set: 테이블 형태의 데이터의 in-memory 표현방식으로 아래와 같은 방식으로 나타낼 수 있다.

  | Record Set <>-------> Table  <>-----> Row and Column

.. code-block:: java

  isFirst(): Is the current row the first row of the Recordset. Return true/false boolean
  isLast(): Is the current row the last row of the Recordset. Return true/false boolean
  hasNext(): Does a row exist after the current row. Return true/false boolean
  moveFirst(): Navigate back to the first row of the Recordset
  moveLast(): Navigate back to the last row of the Recordset
  moveNext(): Navigate to the next row of the Recordset. (Nothing happens if current row is last row)
  

Active Record
-------------
만약에 서비스 로직이 Domain Model로 구성되어 있다면 위의 패턴은 잘 맞지 않다. 이런 경우에는 위의 Row Data Gateway와 도메인 로직을 결합한
'Active Record'패턴이 대안이 될 수 있다.


Data Mapper
-----------
Active Record와 달리 도메인 객체와 테이블 사이의 매핑관계를 설명해주는 역할을 하는 것은 'Data Mapper' 라고 한다.

