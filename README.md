# EFK 스택 구축
1.fluentd-config 로그 파서 설정
각 로그 이벤트의 형식을 정의
format1은 첫 번째 줄의 로그 이벤트 형식을 정의
/^(?<time>\d{4}-\d{1,2}-\d{1,2} \d{1,2}:\d{1,2}:\d{1,2}.\d{3}) (?<level>[^\s]+) \[(?<thread>.*)\] \[(?<classname>.*)\] (?<message>.*)/
(?<time>\d{4}-\d{1,2}-\d{1,2} \d{1,2}:\d{1,2}:\d{1,2}.\d{3}): 로그의 시간 부분을 캡처 ex) 2024-06-07 08:00:40.249
(?<level>[^\s]+): 로그 레벨을 캡처 ex) info
\[(?<thread>.*)\]: 스레드 정보를 캡처. ex) [main-thread]
\[(?<classname>.*)\]: 클래스 이름을 캡처 ex) [com.example.MyClass]
(?<message>.*): 로그 메시지를 캡처 ex) Skipping auto-sync: most recent sync already to 9db9771c835bd02e46adf3c3aa794d77f2987b52

2. Kibana 인덱스 패턴 생성
http://localhost:30561/ 로 접속
   management -> kibana -> Index Patterns
   logstash-* 입력
![kibana1](https://github.com/dooz1e/efk/assets/170922638/83ce7361-f190-4dac-9128-f7038878f2b9)
  @timestamp 선택
![kibana2](https://github.com/dooz1e/efk/assets/170922638/04cfbf8c-3dc2-4147-b6b3-2a0b720ca541)
원하는 키워드로 로그 검색가능
![kibana-solr](https://github.com/dooz1e/efk/assets/170922638/ac091753-482c-472b-acca-69c78b0a417d)
