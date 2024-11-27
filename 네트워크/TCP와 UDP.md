# TCP와 UDP

## TCP

전송을 제어하는 프토토콜
-> 인터넷상에서 데이터를 메세지의 형태로 보내기 위해 IP와 함께 사용하는 프로토콜

TCP는 IP와 함께 인터넷의 기반을 이루는 프로토콜로, TCP/IP라고도 부른다. 

둘은 pair로 사용되는 프로토콜이다.

### TCP의 특징

1. 연결형 서비스
2. 신뢰성 있는 프로토콜
3. 흐름제어 및 혼잡제어
4. 오류검출 및 재전송
5. 전이중, 점대점 방식(전이중: 데이터를 양방향으로 동시에 전송 가능, 점대점: 통신이 두 점 사이에서만 이루어짐)



### TCP의 연결
3-way handshaking을 통해 연결을 설정하고, 4-way handshaking을 통해 연결을 해제


### TCP의 흐름제어 및 혼잡제어
흐름제어: 수신자와 송신자의 데이터 처리 속도 차이를 조절하는 것
혼잡제어: 네트워크 내의 패킷 수가 넘치지 않도록 방지하는 것

### TCP의 사용
- 파일 전송
- 이메일

### TCP의 헤더 구조
```c
struct tcp_header {
    unsigned short source_port; // 송신지 포트 번호
    unsigned short dest_port; // 수신지 포트 번호
    unsigned int seq_num; // 순서 번호
    unsigned int ack_num; // 확인 번호
    unsigned char header_len; // 헤더 길이
    unsigned char flags; // 플래그
    unsigned short window_size; // 윈도우 크기
    unsigned short checksum; // 체크섬
    unsigned short urgent_pointer; // 긴급 포인터
}
```



## UDP

비연결형 서비스

데이터를 데이터그램 단위로 처리하는 프로토콜

### UDP의 특징

1. 비연결형 서비스
2. 신뢰성이 낮다
3. TCP보다 속도가 빠르다
4. 헤더의 checksum 필드를 통해 최소한의 오류만 검출
5. 점대점이 아닌 멀티캐스팅, 브로드캐스팅을 지원


### UDP의 사용
- 실시간 게임
- 스트리밍 서비스

### UDP의 헤더 구조
```c
struct udp_header {
    unsigned short source_port; // 송신지 포트 번호
    unsigned short dest_port; // 수신지 포트 번호
    unsigned short length; // 길이
    unsigned short checksum; // 체크섬
}
```



