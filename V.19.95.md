# v19.95

## 용어 정리
1. A record
   - Domain 이름에 IP 주소를 매핑 
   - 113.232.132.13

2. CNAME
   - 서브도메인
   - www.testous.com -> testous.com

3. payload
   - 전송되는 데이터


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

## SQS, SWF, SNS
### SQS (Simple Queu Service)
- 분산 시스템 및 서버시르 애플리케이션을 위한 `완전 관리형 메시지 대기열`
- 마이크로 서비스 사용 가능
- 서버 측 암호화(SSE)를 통해 각 메시지 본무을 암호화 하여 애플리케이션에 완전히 전달
- AWS KMS와 통합하여 암호화 제공, SQS메시지를 보호하는 키를 `중앙에서`관리
- `pull`방식, `push`하지 않는다
- FIFO
  
### SWF (Simple Work Flow)
- 백그라운드 작업을 `병렬 혹은 `순차`방식으로 실행
- 분산 애플리케이션 컴포넌트를 코디네이트 해주는 `웹 서비스`
- 미디어 프로세싱 e.g)동영상 인코딩
- 웹 애플리케이션 백엔드, 애널리틱스 파이프라인, 워크플로 등

### SNS (Simple Notification Service)
- 엔드 포인트 프로토콜 : Http(s), 이메일(SMTP), SMS, SQS, Lambda 등
- 전송된 메시지는 동일한 리전의 복수 가용 영역으로 복제
- 즉각적은 , 푸시 방식 전달 
- 간단한 API, 쉬운 개발단과 통합
- 다양한 전달 프로토콜에 적용 가능
- 관리 콘솔에서 web방식으로 설정
- e.g.2) 이미지 업로드 이후 작업을 SNS로 제어하기
    - S3 이미지 업로드 -> 이벤트 발생 -> AWS SNS호출 -> 이미지 업로드 Topic 발행 -> Subscriber 병령 구독 
    - AWS SES -> 이미지 업로더에게 확인 메일 발송
    - AWS SQS -> 이미지 리사이징 작업을 큐에 추가
    - AWS Lambda ->Amazon Rekognition을 구동하여 이미지 인식
  
### SNS vs. SQS
- 둘 다 메시징 서비스
- SNS 푸시 방식, SQS pull 방식

### SQS vs. SWF
- SQS : Message oriented API, 14일간 메시지 유지, 메시지는 중복될 수도 있다. 추가 모니터링 필요
- SWF : Task oriented API, 1년간 워크 유지, task는 `한번 할당`, 모니터링 가능

## AWS S3
### Storage Classes
1. S3 Standard
2.  S3 Infrequently Accesed
    - 자주 접근되지 않지만, 가끔 필요할 때는 빠른 속도로 검색하는 경우를 위한 S3
    - S3 Standard 보다 가격이 저렴하지만, retrieval fee(검색 비용)이 따로 요구됨
3. S3 One-Zone-Infrequent Access
   - 단일 가용 영역에 객체를 저장하도록 선택
   - 단일 가용 영역 내에 데이터를 중복으로 저장, 지리적으로 분리된 여러 가용 영역 전체에 데이터를 중복 저장
   - 가용영역이 파괴시 데이터 손실
   - 백업 복사본, 재해 복구 복사본, 손쉽게 재생성 가능한 데이터, 자주 엑세스 하지 않는 스토리지
4. S3 Standard-Infrequent Access 
   - 엑세스 빈도가 낮지만 필요할 때 빠르게 엑세스해야하는 데이터
   - 장기 파일 스토리지, 이전 동기화 및 공유 스토리지, 다른 오래된 데이터에 적합
5. S3 Inteligent-Tiering
    - 분석 기법을 이용해 데이터를 비용 최적화된 클래스로 자동으로 옮겨준다.
    - 두 엑세스 티어에 객체를 저장
    - 하나는 Frequent Access
    - 다른 하나는 비용이 낮은 Infrequent Access
    - 짧은 지연 시간 높은 처리량 제공
6. S3 Glacier
  - 장기적인 백업 전용
  - 높은 durability(내구성)

