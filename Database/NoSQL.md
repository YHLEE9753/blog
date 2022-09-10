# NoSQL
2022/09/06

# NoSQL
https://hanamon.kr/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-sql-vs-nosql/
## 정의
- 관계형 데이터베이스가 아닌 모든 곳에서는 NoSQL인 것이다
- NoSQL이란 누군가는 ‘non SQL(비 SQL)’의 약자로, 또 누군가는 ‘not only SQL(SQL만을 사용하지 않는)’라는 뜻으로 생각한다.
- NoSQL 데이터베이스(일명 “SQL만을 사용하지 않는 데이터베이스”)는 표 형식이 아니며, 관계형 테이블과는 다른 방식으로 데이터를 저장한다.
- NoSQL 데이터베이스는 SQL 앞에 붙은 ‘No’에서 알 수 있듯이, 주로 데이터가 고정되어 있지 않은 데이터베이스를 가리킨다.
- NoSQL 데이터베이스는 데이터 모델에 따라 유형이 다양하다.
- 주요 유형으로는 문서, 키 값, 와이드 컬럼, 그래프가 있다.
- NoSQL이 SQL과 반대되는 개념처럼 사용된다고 해서, NoSQL에 스키마가 반드시 없는 것은 아니다.
- 이들은 유연한 스키마를 제공하며, 대량의 데이터와 높은 사용자 부하에서도 손쉽게 확장이 가능하다.
- 관계형 데이터베이스에서는 데이터를 입력할 때 스키마에 맞게 입력해야 하는 반면, NoSQL에서는 데이터를 읽어올 때 스키마에 따라 데이터를 읽어 온다.
- 이런 방식을 ‘schema on read’라고도 한다.
- 읽어올 때에만 데이터 스키마가 사용된다고 하여, 데이터를 쓸 때 정해진 방식이 없다는 의미는 아니다. 
- 데이터를 입력하는 방식에 따라, 데이터를 읽어올 때 영향을 미친다.

## 저장방식에 따른 분류
### Key-Value Model
속성을 Key-Value의 쌍으로 나타내는 데이터를 배열의 형태로 저장한다.
여기서 Key는 속성 이름을 뜻하고, Value는 속성에 연결된 데이터 값을 의미한다.
Redis, Dynamo 등이 대표적인 Key-Value 형식의 데이터베이스이다.

### Document Model
데이터를 테이블이 아닌 문서처럼 저장하는 데이터베이스를 의미한다.
많은 문서형 데이터베이스에서 JSON과 유사한 형식의 데이터를 문서화하여 저장한다.
각각의 문서는 하나의 속성에 대한 데이터를 가지고 있고, 컬렉션이라고 하는 그룹으로 묶어서 관리한다.
대표적인 문서형 데이터베이스에는 MongoDB 가 있다.

### Column Model
데이터베이스의 열(column)에 대한 데이터를 집중적으로 관리하는 데이터베이스이다.
각 열에는 key-value 형식으로 데이터가 저장되고, 컬럼 패밀리(column families)라고 하는 열의 집합체 단위로 데이터를 처리할 수 있다.
하나의 행에 많은 열을 포함할 수 있어서 유연성을 높다.
데이터 처리에 필요한 열을 유연하게 선택할 수 있다는 점에서 규모가 큰 데이터 분석에 주로 사용되는 데이터베이스 형식이다.
대표적인 wide-column 데이터베이스에는 Cassandra, HBase 가 있다.

### Graph
자료구조의 그래프와 비슷한 형식으로 데이터 간의 관계를 구성하는 데이터베이스이다.
노드(nodes)에 속성별(entities)로 데이터를 저장한다.
각 노드간 관계는 선(edge)으로 표현한다.
대표적인 그래프 데이터베이스에는 Neo4J, InfiniteGraph 가 있다.

## SQL, NoSQL 차이
👉 데이터 저장(Storage)
NoSQL은 key-value, document, wide-column, graph 등의 방식으로 데이터를 저장한다.
관계형 데이터베이스는 SQL을 이용해서 데이터를 테이블에 저장한다.
미리 작성된 스키마를 기반으로 정해진 형식에 맞게 데이터를 저장해야 한다.
👉 스키마(Schema)
SQL을 사용하려면, 고정된 형식의 스키마가 필요하다.
다시 말해, 처리하려는 데이터 속성별로 열(column)에 대한 정보를 미리 정해두어야 한다.
스키마는 나중에 변경할 수 있지만, 이 경우 데이터베이스 전체를 수정하거나 오프라인(down-time)으로 전환할 필요가 있다.
NoSQL은 관계형 데이터베이스보다 동적으로 스키마의 형태를 관리할 수 있다.
행을 추가할 때 즉시 새로운 열을 추가할 수 있고, 개별 속성에 대해서 모든 열에 대한 데이터를 반드시 입력하지 않아도 된다.
👉 쿼리(Querying)
쿼리는 데이터베이스에 대해서 정보를 요청하는 질의문이다.
관계형 데이터베이스는 테이블의 형식과 테이블간의 관계에 맞춰 데이터를 요청해야 한다.
그래서 정보를 요청할 때, SQL과 같이 구조화된 쿼리 언어를 사용한다.
비관계형 데이터베이스의 쿼리는 데이터 그룹 자체를 조회하는 것에 초점을 두고 있다.
그래서 구조화 되지 않은 쿼리 언어로도 데이터 요청이 가능하다.
UnQL(UnStructured Query Language)이라고 말하기도 한다.
👉 확장성(Scalability)
일반적으로 SQL 기반의 관계형 데이터베이스는 수직적으로 확장하다.
높은 메모리, CPU를 사용하는 확장이라고도 한다.
데이터베이스가 구축된 하드웨어의 성능을 많이 이용하기 때문에 비용이 많이 든다.
여러 서버에 걸쳐서 데이터베이스의 관계를 정의할 수 있지만, 매우 복잡하고 시간이 많이 소모된다.
NoSQL로 구성된 데이터베이스는 수평적으로 확장한다.
보다 값싼 서버 증설, 또는 클라우드 서비스 이용하는 확장이라고도 한다.
NoSQL 데이터베이스를 위한 서버를 추가적으로 구축하면, 많은 트래픽을 보다 편리하게 처리할 수 있다.
그리고 저렴한 범용 하드웨어나 클라우드 기반의 인스턴스에 NoSQL 데이터베이스를 호스팅할 수 있어서, 수직적 확장보다 상대적으로 비용이 저렴하다.

## 언제 MySQL NoSQL?
데이터베이스를 구축하는 방법을 선택하는 것에 완벽한 솔루션은 없다.
그렇기 때문에 많은 개발자들은 유저의 요구를 충족하기 위해 관계형, 비관계형 데이터베이스를 모두 사용하여 서비스에 맞게 설계하고 있다.
NoSQL 기반의 비관계형 데이터베이스가 확장성이나 속도면에서 더 뛰어나다.
그러나 고차원으로 구조화된 SQL 기반의 데이터베이스가 더 좋은 성능을 보여주는 서비스도 있다.
여러 사용 사례를 살펴보고 적절한 데이터베이스를 선택하는 것이 중요하다.

### CAP 이론
https://sabarada.tistory.com/91
- 일관성 
- 가용성
- 네트워크 분할 허용성



- 동시성 제어
    - 동시성 제어를 하지 않을 시 발생하는 문제점
    - 동시성 제어 방법
- Join
- https://pearlluck.tistory.com/46
- https://doh-an.tistory.com/30
- 
    - Inner Join
    - Natural Join
    - Outer Join
    - Semi Join
- 스키마(Schema)
- https://coding-factory.tistory.com/216
    - 스키마 3계층과 3계층으로 나누어 사용하는 이유
    - 테이블 vs 스키마