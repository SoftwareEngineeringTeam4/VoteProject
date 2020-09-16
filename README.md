# 프로젝트 주제 #

정기총회, 과 및 학생회 선거 등 교내에서 사용 가능한 전자 투표 어플리케이션 개발

# Problem Statement #
- 전자투표 시스템이 제공하는 기능을 사용하는 주체
   - 본교 학생
- 시스템의 기능을 제공하기 위해 활용해야 하는 외부 시스템
   - 본교 종합정보시스템 Authentication, Firebase(Cloud Firestore), MySQL, AWS EC2

https://www.hankyung.com/society/article/201912300729i
기사에 따르면 여러 대학이 총학생회 내지 교내 선거에 대해 투표율 저조로 인해 선거의 무산, 선거 후보자, 안건에 대한 무관심으로 어려움을 겪고 있고 이는 비단 타 학교만의 문제가 아닌 우리 학교에서도 겪고 있는 문제이다.
즉, REV(Remote E-Voting) 방식의 전자투표 방식을 채택하여 투표장을 가지 않아도 투표를 할 수 있도록 하여 학생들 입장에서도 투표에 대한 거부감을 덜 뿐 아니라 주최하는 입장에서도 개수를 하지 않아도 되므로 시간적 소요를 덜 수 있다.

->  학생들은 다음과 같이 두 가지 전자 투표 기능을 사용할 수 있다.
1. 안건 투표 기능
   - 학생 총회 또는 동아리 연합회 대표자 회의 등에서의 안건 찬/반 투표를 기존 거수로 진행하던 방식에서 전자 투표 방식으로 사용
2. 선거 투표 기능
   - 총학생회 선거, 과회장 선거 등 선거에서 후보자 투표를 위한 전자 투표 기능

# Functional Requirements # 
- 신원 인증을 위한 종합정보시스템 Authentication 사용
- 1인 1투표를 위한 중복 로그인 방지 시스템이 존재 (세션 사용)
- 투명성을 보장하기 위한 실시간 투표율 및 진행 과정을 확인 (socket.io)
- 후보자의 정보를 저장하기 위해 RDBMS 사용 (MySQL)
- 안건의 내용 혹은 부가 정보를 저장하기 위해 Cloud Firestore 사용
- 투표방 개설, 질문 및 항목에 대한 다양한 입력
- 안건 및 후보자에 대한 정보 등록 및 삭제, 조회 가능
- 투표 결과에 대한 엑셀 출력 및 다운로드

# Nonfunctional Requirements #
- 학생들은 투표를 되돌릴 수 없으면 투표 횟수는 1회로 제한
- 로그인 시간은 10분을 넘기지 않는다
- 편리하게 서비스하기 위한 자동 로그인 기능 지원
- 유학생을 위한 한국어, 영어 등 다국어 모드를 지원 (Usability)
- 사용 중, 오류가 발생하면 오류 문구와 함께 관리자에게 건의를 해달라는 문구 출력 (Usability) 
- 안건을 보여주는데 걸리는 시간은 3초 이내 (Performance - Response time)
- 약 1000명이 동시 접속을 할 수 있어야한다 (Performance - Throughput)
- 투표 결과를 저장하는 엑셀파일의 크기는 1MB보다 작아야한다 Performance - Scalability)
- 모든 브라우저에서 정상적으로 작동 (웹앱의 경우) (Supportability - Adaptability)
- 시스템 배포 이후에도 유지보수가 가능(Supportability - Maintainability)
- 사용자의 투표정보를 다른 사용자나 관리자가 볼 수 없도록 한다 (Legal - Regulation)
- 투표 기간이 끝날 때까지 선거 결과에 액세스 할 수 없다

# 팀 구성원, 역할 및 역량 #

|Participant|Roles|Skills|Training Needs|
|------|---|---|---|
|허호녕|Team Leader, Implementator| Programming : C, C#, Node.js <br> Firebase, Flutter | UML modeling, Communication Skills |
|김민수|Implementor, Requirement engineer| Programming : C, C#, Python, Django <br> Flutter, Firebase, MySQL | UML modeling, Node.js framework|
|최원혁|Implementor, Cloud Architect| Programming : C++, C#, Python, Node.js <br> Express.js, Flutter, Firebase, MonogoDB, MySQL, UWP | UML modeling, Cloud Architecture |
|유승민| Configuration manager| Entity relationship <br> Databases : relational, SQLite <br> Document Management| UML modeling <br> Programming : C, Java |
|이산가 비두샤|UX/UI Implementor| Programming : Python, C, Dart, Java <br> Software : Adobe XD | UML
