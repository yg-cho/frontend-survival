# 데이터

### REST API

{% hint style="info" %}
Backend에서 JSON형태의 데이터를 돌려주는 API를 제공한다고 가정한다(대부분 REST or GraphQL)
{% endhint %}

#### REST - Representational State Transfer의 약자로 자원을 이름으로 구분하여 해당 자원의 상태를 주고 받는 것을 의미

1. HTTP URI(Uniform Resource Identifier)를 통해 자원(Resource)를 명시
2. HTTP Method(POST, GET, PUT, DELETE 등)을 사용
3. 해당 자원(URI)에 대한 CURD(Create, Update, Read, Delete)

* GET - URL에 데이터를 포함(Query)하여 데이터 조회
* POST - Body에 데이터를 포함하여 데이터 생성
* PUT - Body에,데이터를 포함하고,  기존 데이터를 업데이트
* DELETE - 데이터를 삭제

#### GraphQL - 그래프형태의 쿼리를 사용하여 원하는 데이터를 요청

1. Graph 자료구조형
2. URI명시 없이 얻고자 하는 데이터를 Query로 지정

* Query(Read)
* Mutation(Create, Update, Delete)
* Subscription(Event)



#### REST의 특징

1. Server - Client 구조
2. Stateless (무상태)
3. Cacheable (캐시 처리 가능)
4. Layered System (계층화)
5. Uniform Interface (인터페이스의 일관성)

#### GranphQL의 특징

1. 한번의 요청으로 원하는 모든 데이터를 서버로부터 받아온다
