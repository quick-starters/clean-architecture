# clean-architecture
만들면서 배우는 클린 아키텍처 스터디

## 5~7장 스터디 논의 내용
🗣 지현 : 한 스키마에 컬럼이 4~5개 있다. 컬럼에다 바이너리 형태로 변환해서 저장하고 있다. 하나의 오브젝트가 바이너리로 변환되서 저장되는 형태. 헥사고날 하다가 기존 레파지토리 참조하는 것을 오프라인이 지원되는데 큐를 쌓아서 한번에 요청을 보낸다. 매번 디비에 접근하는게 비효율적이라 판단되서 인 메모리로 캐싱한다. (클라이언트에서 오프라인 요청을 보낼 때이다.) 인메모리는 인메모리 디비가 아닌 머신의 메모리, 힙을 쓴다. 이 때 어댑터에 놓을까?
🗣 혁진 : 저는 어댑터에 놓습니다. 인메모리가 레디스나 영구 저장 디비로 바꿀 때도 어댑터만 바꾸게. 팀이 다 그렇다면 그렇게 할수도 있을 것 같습니다. 그냥 레디스를 쓰자를 밀어 붙여보자.
🗣 종민 : 무조건 어댑터일 것 같습니다. 인메모리 해시맵 이런게 아니고 라이브러리 쓰시지 않을까요? 메모리에 캐시한다는게 유스케이스가 아예 다른가요? 요청이 들어오면 캐시 먼저 찔러보는게 아니고 바로 해당 유스케이스에 찌르는거죠?
🗣 혁진 : 차라리 캐싱을 스프링처럼 프록시로 만들어서 어댑터로 사용하지 않는 방법도 있을 것 같다.
🗣 종민 : 저는 DB 조회를 캐시 쪽으로 넣어서 델리게이트 패턴을 쓸 것 같아요

