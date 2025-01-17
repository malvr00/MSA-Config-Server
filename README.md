# MSA-Config-Server
- 사용 기술
  - RabbitMQ
  - Spring boot bus (amqp)
  - Srping boot actuator
- 사용 이유
  - Microservices Architecture(MSA)에서 각 서비스가 개별적인 설정 파일을 관리하면 일관성 유지가 어렵고, 설정 변경 시 서비스마다 수동 업데이트가 필요합니다.
  - 이를 해결하기 위해 Spring Cloud Config Server를 두어 설정을 중앙 집중식으로 관리하면, 아래와 같은 문제를 해결할 수 있습니다.
    - 모든 서비스가 동일한 성정을 공유할 수 있음.
    - 설정을 쉽게 변경하고 적용할 수 있음.
    - Git과 같은 외부 저장소와 연동하여 버전관리도 가능하다.
- 프로젝트
  - Config server 메인 [[이동]](https://github.com/malvr00/MSA/blob/master/lab1/config-service/src/main/resources/application.yml)
  - 연동 프로젝트 [[이동]](https://github.com/malvr00/MSA/blob/master/lab1/user-service/src/main/resources/bootstrap.yml)

