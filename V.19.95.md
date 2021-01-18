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

4. Amazon machine image (AMI)
   - 인스턴스의 루트 볼륨용 템플릿 (운영체제등)
   - 주로 Auto Scaling 이용

5. Port 443 
   - 0 0 0 0 /0
   - 외부접속 허용 
   - https의 기본 포트
   - 인증서 기반 클라이언트 인증

6. port 1433
   - Microsoft SQL Server 기본 포트

7. cross-origin resource sharing(CPORS)
   - 웹 페이상의 제한된 리소스를 최초 자원이 서비스된 도메인 밖의 다른 도메인으로부터 요청할 수 있게 허용하는 구조
   - 즉, 추가 HTTP헤더를 사용하여, 한 출저에서 실행 중인 웹 애플리케이션이 다른 출저의 선택한 자원에 접근할 수 있는 권한을 부여하도록 브라우저에 알려주는 체제

8. AWS Step Functions
   - 워크플로 관리 및 AWS서비스들을 조합하는 플랫폼
   - 고가용성, 확장성
   - TASK를 생성하고, 순차적인 처리 단계fmf wlwjd
   - 시각적 차트를 통해 Flow와 현재 상태에 대한 이해 제공

9. Storage Gateway 
    -  온프레미스 소프트웨어 어플라이언스 클라이드  기반 스토리지와 연결
    -  file gateway : 수명주기 정책, 지역 간 복제 및 버전 관리를 사용하여 S3데이터를 관리 가능 / 데이터에 직접 액세스 가능
    -  volume gateway : 캐싱 / 저장 볼륨
       -  캐싱볼륨 : 자주 액세스하는 데이터에 액세스 
       -  저장볼륨 : 지연 시간이 낮은 액세스가 필요한 경우 먼저 모든 데이터를 로컬로 저장하도록 온프레미스 게이트웨이를 구성 / 스냅샷저장,
<img src="(https://user-images.githubusercontent.com/45276804/104834933-6549f480-58e6-11eb-9b6a-8c92726dd5da.png">
10. AWS Batch
    - EC2 인스턴스를 사용하여 배치 형태의 task를 생성, 관리하는 관리 도구
    - Spot 혹은 `On-Demand 형태`의  vCPU가 포함된 Compute 환경 생성
    - 우선순위에 따라 Job Queue 생성하고 Compute에 할당
    - Job에 대한 선언은 스크립트, JSON, 환경 변수, 마운트 지점, IAM역할, 컨테이너 이미지등을 포함
    - Job에 대한 스케줄링

<img src="https://user-images.githubusercontent.com/45276804/104834923-49dee980-58e6-11eb-9e43-b1d62f5c4e28.png">

11. Migration HUb
    - 마이그레이션 도구가 제공되는 모든 AWS리전의 마이크레이션을 `모니터링` 할 수 있는 단일 장소를 제공
    - 사용하는데 따른 추가 비용 없음

12. Origin Access Identity 
    - 접근을 제어하여 보안을 강화
    - CloudFront, S3 등의 접근만을 허용가능하도록 구성 가능

13. Cold Data
    - 가끔식만 엑세스하거나 더 이상 적극적으로 사용하지 않는 데이터
    - 보통 이 데이터를 사용할때는 스피드가 중요시 되지 않는 경우 이용

14. Hot Data
    - Cold Data에 반대로 즉각적인 엑세스와 최고급의 스토리지가 필요

15. NAT Gateway
    - public subnet에두어 엔드포인트를private subnet에 두면 private subnet 인스턴스들을 외부 접속이 가능해짐
    - 그러나 반대로, 외부에서는 접근 불가

16. VPC End Point
    - 인터넷 게이트웨어, NAT, VPN, AWS Direct connect의 연결을 필요로 하지 않고 privateLink 구동 지원 AWS 서비스 및 VPC엔드포인트 서비스에 비공개로 연결 가능
    - 이 엔드포인트를 이용하면 VPC와 기타 서비스간의 트래픽은 Amazon네트워크를 벗어나지 않는다.



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
1. ElastiCache
   - Redis 또는 Memcached와 호환되는 관리형 인 메모리 데이터 스토어
   - 오픈 소스와 호환되는 인메모리 데이터 스토어를 원할하게 배포, 실행 및 확장
   - 처리량이 많고 지연시간이 짧은 인 메모리 데이터 스토어에서 데이터를 검색하여 데이터 집약적 앱을 구축하거나 앱 성능 개선
   - 게임, 광고 기술, 금융 서비스, 의료 서비스 및 IoT 앱에서 많이 사용됨
   - 데이터 복제를 통한 높은 가용성과 성능속도
   - 데이터가 비교적 동일하게 유지 또는 빠르게 변경 가능
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
7. S3 versioning (버전 관리)
   - 의도치 않은 사용자 작업과 응용 프로그램 오류 모두에서 쉽게 복구 가능
   - 활성화 시 S3 가 동일한 객체에 대해 여러 쓰기 요청을 동시에 수신하면 모든 객체를 저장
   - S3에 버킷에 모든 객체의 모든 버전을 보전, 검색 및 복원


## Storage
### Storage optimized instances withe instance store
- 로컬 스토리지의 매운 큰 데이터 세트에 대한 높은 순차 읽기 및 쓰기 엑세스가 필요한 워크로드를 위해 설게됨
- 지연시간이 짧은 수만 개의 IOPS를 애플리케이션에 제공하도록 최적화
### Amazon EFS (Elastic File System)
- EC2 인스턴트용 파일 스토리지
- EC2 인스턴스에서 공유 가능한 파일 스토리지
- 멀티 AZ 에 대응
- 빅데이터 분석, 웹 서빙, 내용 관리, 어플리케이션 테스트, 워크플로,데이터베이스 백업 등

### FSx
- Microsoft Windows 기반 스토리지 (Lustre와 Window File Server)
- 고성능 컴퓨팅(HPC), 기계 학습 및 전자 설계 자동호와 같은 워크로드에 대한 호환성 및 기능을 제공
- 쉽고 비용 효율적이다.

### EBS
- EC2 인스턴스에서 파일시스템용으로 사용되는 블록 스토리지
- 데이터에 빠르게 엑세스하고 장기적으로 지속해야 하는 경우 사용
- EBS Provisioned IOPS SSD(io1) : I/O 특성 좋은 것으로 NoSQL and relational databaeses 등 사용
- EBS General Purpose SSD(gp2) : 부팅 빠르고 latency에 좋음
- Throughput Opimized HDD(st1) : 빅데이터와 같은 곳으로 내부 처리량이 많은 것에 사용
- Cold HDD(sc1) : 모니터링과 같은 하루 단위로 필요한 경우로 사용량인 적은 경우
- Magentic : 가격이 가장 싼 경우에 사용

### Snowball
- 테라바이트 또는 페타바ㅣ트 규모의 데이터를 AWS와 주고 받는 서비스
- 인터넷 연결이 곤란한 장소에서 `비용 효율적`으로 AWS 클라우드의 스토리지 및 컴퓨팅 파워에 엑세스가능

## 보안 자격
### AWS WAF
- CloudFront 배포 또는 ALB로 전달되는 웹 요청을 `모니터링`하는 웹 어플리케이션 방화벽
- 사용자가 지정하는 조건(요청을 송신한 IP주소 또는 요청의 값)에 따라 요청을 `차단`


## 분석
### AWS Glue
- 고객이 분석을 위해 손쉽게 데이터를 준비하고 로드할 수 있게 지원하는 완전관리형 ETL(추출, 변환 및 로드) (프레임워크)
- 효율적인 비용으로 간단하게 원하는 데이터를 분류, 정리, 보강하고 다양한 데이터 스토어 간에 이동
- `S3` 와 연결하여 쿼르 편집 가능

### Amazon Kinesis
- `실시간 스트리밍 데이터`를 손쉽게 수집, 처리 분석할 수 잇으므로 적시에 통찰력을 확보하고 새로운 정보에 신속하게 대응
- `모든 규모의 스트리밍 데이터`를 비용 효율적으로 처리할 수 있는 핵심 기능과 더불어 애플리케이션 요구 사항에 가장 적합한 도구를 선택할 수 있는 유연성 제공


## 데이터베이스
### DynamoDB
- NoSQL 데이터베이스 서비스로 확장성과 빠르고 예측 가능한 성능을 제공
- 데이터 규모와 관계없이 데이터를 저장 및 검색하고, 어떤 수준의 요청 트래픽이라도 처리할 수 있는 데이터베이스 테이블을 생성할 수 있음.
- 문서 모델과 Key-Value 스토어 모델을 지원하는 NoSQL데이터베이스

## Redshift
- 기존 비즈니스 인텔리전스 도구를 사용하여 모든 데이터를 간단하고 비용 효율적으로 분석할 수 있도록 지원하는 페타바이트 규모의 빠른 완전관리형 데이터 웨어하우스 서비스
- 몇백 GB부터 페타바이트 규모 이상의 데이터 세트에 최적화
- 태그설정 가능