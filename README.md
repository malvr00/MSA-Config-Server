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

## RabbitMQ
Spring Cloud Bus를 이용해 설정 변경 사항을 각 서비스에 알리려면 메시지 브로커가 필요합니다. 그래서 RabbitMQ를 선택했는데 이유는 아래와 같습니다.
- RabbitMQ 선택 이유
  - Spring Cloud Bus와의 호환성
    - Spring Cloud Bus는 Kafka와 RabbitMQ를 지원하는데, **RabbitMQ는 설정이 간단하고 경량 메시지 브로커** 로 적합합니다.
  - 비동기 이벤트 기반 업데이트 가능
    - 서비스들이 설정 변경 이벤트를 비동기적으로 수신하므로, 서버를 재시작하지 않고도 설정을 반영할 수 있습니다.
  - 빠른 메세지 전송 속도 및 안정성
    - Config Server에서 설정 변경 이벤트를 발생시키면 RabbitMQ가 빠르게 메시지를 전달하여 다른 서비스들이 즉시 감지하고 업데이트 가능합니다.
