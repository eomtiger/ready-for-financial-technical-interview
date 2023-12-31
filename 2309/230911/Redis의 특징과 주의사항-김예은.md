### Redis란?
- key, value 구조의 비정형 데이터를 저장하고 관리하기 위한 오픈 소스 기반의 비관계형 데이터베이스 관리 시스템입니다.
- 데이터베이스, 캐시, 메세지 브로커로 사용되며 인메모리 데이터 구조를 가진 저장소입니다.
- db-engines.com에서 key, value 저장소 중 가장 순위가 높습니다.

### Redis의 특징
- key,value 구조이기 때문에 쿼리를 사용할 필요가 없습니다.
- 데이터를 디스크에 쓰는 구조가 아니라 메모리에서 데이터를 처리하기 때문에 속도가 빠릅니다.
- String, Lists, Sets, Sorted Sets, Hashes 자료 구조를 지원합니다.

String : 가장 일반적인 key- value 구조의 형태입니다.
Sets : String의 집합입니다. 여러 개의 값을 하나의 value에 넣을 수 있습니다. 포스트의 태깅 같은 곳에 사용될 수 있습니다.
Sorted Sets : 중복된 데이터를 담지 않는 set 구조에 정렬 Sort를 적용한 구조로 랭킹 보드 서버 같은 구현에 사용할 수 있습니다.
Lists : Array 형식의 데이터 구조입니다. List를 사용하면 처음과 끝에 데이터를 넣고 빼는 건 빠르지만 중간에 데이터를 삽입하거나 삭제하는 것은 어렵습니다.
  - single Threaded입니다. 한번에 하나의 명령만 처리 가능합니다. 중간에 처리 시간이 긴 명령어가 들어오면,그 뒤 명령어들은 대기가 필요합니다. (get, set의 경우는 초당 10만 개 이상 처리 가능할 정도로 속도가 빠릅니다.)

### Redis 주의할 점
- 서버에 장애가 발생했을 경우 그에 대한 운영 플랜이 꼭 필요합니다. 인메모리 데이터 저장소의 특성상, 서버에 장애가 발생했을 경우 데이터 유실이 발생할 수 있기 떄문입니다.
- 메모리 관리가 중요합니다.
- 싱글 스레드 특성 상, 한 번에 하나의 명령만 처리할 수 있습니다. 처리하는 데 시간이 오래 걸리는 요청/ 명령은 피해야합니다.