# Spec
1. 개요
    * 목표
       * 사용자의 위치를 기록하는 앱
    * 문서규칙 
       * 없음
    * 대상 독자 및 읽는 방법
       * 개발자
    * 프로젝트 목표
       * 목표를 충족하는 기능을 개발하고 App Store 및 Play Store에 배포
    * 관련 문서
       * 없음
    * 정의 및 약어
       * 없음
    * 프로젝트 산출물
       * GitHub, https://github.com/hyonsok5/WhereUWereXXX   
1. 전체 설명
    * 제품 조망
       * <img src="https://github.com/hyonsok5/WhereUWereDoc/blob/main/AppFrontendDesign/Contents%20List%20N%20Detail%20Page.png?raw=true" />
    * 전체 시스템
       * 인프라 구성도
          * <img src="https://github.com/hyonsok5/WhereUWereDoc/blob/main/InfraD-WhereUWere.png?raw=true" />
       * Entity-Relationship Diagram
          * <img src="https://github.com/hyonsok5/WhereUWereDoc/blob/main/ERD-WhereUWere.png?raw=true" />   
    * 동작 방식
       * Mobile Device Location 정보를 Mobile Device Local DB에 저장 및 조회
    * 주요 기능
       * Mobile Device에서 사용자의 현재 위치를 기록하고 보여줌
       * 데이터 조작을 방지하기 위해 지우는 기록은 없음
    * 사용자 계층과 특징
       * EveryOne
    * 가정과 종속관계
       * iOS, Android Device Only
    * 단계별 요구사항
       * 없음
    * 하위 호환성
       * iOS, Android Device 2018년 이후 모델 지원  
1. 환경
    * 운영 환경
       * Azure Infra (배포)
       * Redmine Issue Tracker in AWS
       * CI/CD with Git Actions
    * 제품 설치 및 설정
       * 제품 개발
          * Slack (채팅)
          * Visual Studio (IDE)
          * Balsamiq MockUp (화면 디자인 목업)
          * Terraform (인프라 코드)
          * PostMan (REST API Test)
          * Python (백엔드 로직)
          * React (프런트엔드 화면)
          * DBeaver (ERD & Database 처리)
          * AndroidAssetStudio (https://romannurik.github.io/AndroidAssetStudio/)
          * AppIcon (https://appicon.co/)
          * Std. SQL (데이터베이스 Query)
          * Lucid Chart (DB Modeling, Infra Diagram)
          * ECMAScript7 (Frontend)
          * TypeScript (Frontend)
          * HTML (Frontend)
          * Node.js (백엔드)   
    * 배포환경
       * Backend Infra to Azure
       * Docker Hub (배포 이미지 저장)
       * Terraform Cloud App (인프라 배포)
    * 테스트 환경
       * RPA 테스팅 모듈 도입 고려중
       * React Hook은 별도 폴더로, 유닛테스트도 집어넣어야
    * 형상관리
       * GitHub
    * 버그 트래킹
       * Redmine
    * 기타 환경
       * Project Management with Redmine
1. 외부 인터페이스 요구사항
    * 시스템 인터페이스
    * 사용자 인터페이스
    * 하드웨어 인터페이스
    * 소프트웨어 인터페이스
    * 통신 인터페이스
       * REST API
       * HTTPS
       * POST
    * 기타 인터페이스
1. 성능 요구사항
    * 작업 처리량
    * 동시 세선
       * 로컬작업일 경우 제한 없음
       * 클라우드 인프라 작업일 경우 동시 세션 100명. 동시세션수를 초과하면 잠시 후 시도 및 현재 세션수 표시
    * 대응시간
       * 모든 CRUD 기능은 3초 이내 처리되어야 함 
    * 성능 종속관계
    * 기타 성능 요구사항
1. 기능 외 요구사항
    * 안전성 요구사항
       * Backend REST API의 경우 초당 100번의 동시 호출이 오더라도 에러없이 처리되어야 함. (No 5xx Error)
    * 보안 요구사항
       * 사용자 비밀번호 및 이메일 주소 및 위치데이터는 모두 암호화 되어 저장되어야 함. 최소 AES 이상 암호화 알고리즘
       * DB에 저장할 때는 컬럼 암호화를 사용함
       * 로컬 디바이스에 저장할 때는 사용자 아이디로 암호화 키를 사용함
    * 소프트웨어 시스템 특성
    * 데이터베이스 요구사항
       * Mobile Device Local DB를 사용함
    * 비지니스 규칙
    * 설계와 구현 제한사항
       * 날짜/시간은 모두 UTC로 저장한다.
    * 메모리 제한사항
    * 운영 요구사항
    * 사이트 적용 요구사항
    * 다국어 지원 요구사항
       * 영어, 한국어 두개만을 지원함. 기본은 영어
    * 유니코드 지원
       * UTF8을 지원함
    * 64비트 지원
    * 제품인증
    * 필드테스트
    * 기타 요구사항
1. 기능 요구사하
    * 처리중 표시 (CRUD)
       * 프로그레시브 바 표시 필수
    * 비밀번호 입력
       * 입력값 그대로 표시 또는 *** 처리 선택할 수 있게 함
       * 비밀번호 사이즈는 8자리 이상 (특수문자, 대문자, 소문자, 숫자를 조합해야 함)
    * 위치 저장간격
       * 1분 ~ 1시간 사이 선택가능함
    * 데이터 클라우드 저장
       * 사용자 동의를 반드시 받아야 함
    * 예외 사항
       * 자동차로 이동하는 내역은 이동경로에는 표시하나 머물렀던 지점에는 등록하지 않아야 함.    
1. 변경관리 프로세스
    * Frontend, Backend 모두 Dev Branch에서 작성 후 Commit
    * Dev Lead에게 Pull Request 한 후 Slack으로 검토 요청 
    * 만약 Dev Lead가 부재중이거나 급한 상황이면 주변 Contributor 에게 Pull Request & 검토 요청
    * 아주 급한 상황이면 Self Pull Request & Merge to Prod Branch 후 사후 검토 요청
1. 최종승인자
    * Dev Lead
1. 참고문헌
    * 아직까지 없음
1. 부록 (용어)
    * 아직까지 없음
