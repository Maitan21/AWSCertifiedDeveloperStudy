# v19.95

## 용어 정리
1. A record
   - Domain 이름에 IP 주소를 매핑 
   - 113.232.132.13

2. CNAME
   - 서브도메인
   - www.testous.com -> testous.com

## Route 53
### Routing Policy
1. latency routing policy
   - 사용자로 하여금 서버의 상태 등에 상관없이 유저들이 `평균적으로 빠른 응답속도`를 얻는다
   - 지역에 따라서 응답속도가 다를 수 있지만 이 반응속도에 따라 routing응 사용자에게 응답속도를 기준으로 가장 가까운 곳에 있는 서비스를 받을 수 있도록 해준다.

2. fileover routing policy
   - 주 네트워크와 부 네트워크를 분리하여 주 네트워크에 문제 발생시 부네트워크로 연결

3. geolocation routing policy
   - `위치(지역)`에 따라 가장 가까운  지역으로 라우팅 해주는 방법

4. geoproximity policy
   - Traffic flow -> Traffic policy 를 통해서 아주 복잡한 형태으 지역기반 라우팅 가능

5. multivalue routing policy
   - 트랙픽 ID를 부여하여 이를 가지고 health check 가능

## In - memory database Storage solution
1. ElasticCache
   - Redis 또는 Memcached와 호환되는 관리형 인 메모리 데이터 스토어
   - 오픈 소스와 호환되는 인메모리 데이터 스토어를 원할하게 배포, 실행 및 확장
   - 처리량이 많고 지연시간이 짧은 인 메모리 데이터 스토어에서 데이터를 검색하여 데이터 집약적 앱을 구축하거나 앱 성능 개선
   - 게임, 광고 기술, 금융 서비스, 의료 서비스 및 IoT 앱에서 많이 사용됨
   - 데이터 복제를 통한 높은 가용성과 성능속도