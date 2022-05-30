## WebRTC란?
WebRTC(Web Realtime Communications)는 웹 브라우저 간에 직접적으로(peer to peer) 통신할 수 있도록 설계된 API 입니다. 음성 통화, 영상 통화, P2P 파일 공유 등으로 활용될 수 있습니다. 
WebRTC는 RTP 프로토콜을 이용하여 미디어를 교환합니다.

### RTP 프로토콜
실시간 전송 프로토콜(Real-time Transport Protocol, RTP)은 IP 네트워크 상에서 오디오와 비디오를 전달하기 위한 통신 프로토콜 입니다. 
RTP는 전화, WebRTC, 텔레비전 서비스, 웹 기반 푸시 투 토크 기능을 포함한 화상 통화 분야 등의 스트리밍 미디어를 수반하는 통신, 엔터테인먼트 시스템에 사용됩니다.
RTP는 일반적으로 사용자 데이터그램 프로토콜(UDP)로 동작하며, RTP는 RTCP(RTP Control Protocol)와 결합하여 사용됩니다.

## WebRTC 통신을 하기 위한 기본이론
### IP 변환하기
WebRTC 통신은 P2P 즉 브라우저끼리 직접 맞대면서 데이터를 주고받아야 하기 때문에 통신을 하는 당사자들은 서로의 public IP를 인식하고 있어야 한다. 이를 위해 NAT `Network Address Translation`
를 사용하여 개인의 private IP를 public IP로 1대1 대응시켜 변환을 시킵니다.  
또한 NAT는 공개된 인터넷과 사설망 사이에 방화벽을 설치하여 외부 공격으로부터 네트워크를 보호하는 수단으로 사용됩니다.

### 서로 통신경로 찾기
IP를 변환을 시켰다면 ICE `Interactive Connectivity Establishment` 가 두개의 브라우저가 서로 통신할 수 있는 최적의 경로를 찾아준다. 

### STUN & TURN
STUN 서버는 해당 사용자의 public IP 주소를 확인 역할을 담당한다. 즉 클라이언트가 자신의 public IP를 확인하기 위해서 STUN 서버로 요청을 보내고 public IP값을 받는다. 
그리고 그 값을 이용해 통신을 진행한다.

TURN
턴서버는 스턴서버가 연결에 실패했을때 대안의 개념으로 우리가 사용한 PeerJs 는 stun을 자체적으로 가지고있는데, stun이 불발될 경우 사용되는 turn은 따로 설정해주어야 한다

### 시그널링
WebRTC에서 서로 다른 네트워크에 있는 2개의 디바이스들을 서로 연결하기 위해서는, 각 디바이스들의 위치를 발견하는 방법과 미디어 포맷 협의가 필요합니다. 이 프로세스를 시그널링 signaling이라 부르고 상호 간에 동의된 서버에 연결합니다. 
이 서버는 각 디바이스들이 negotiation(협상) 메시지들을 교환할 수 있도록 중개합니다.

## WebRTC 통신의 서버종류
>https://millo-l.github.io/WebRTC-%EA%B5%AC%ED%98%84-%EB%B0%A9%EC%8B%9D-Mesh-SFU-MCU/
>https://6987.tistory.com/entry/WebRTC-%EB%AF%B8%EB%94%94%EC%96%B4-%EC%97%B0%EA%B2%B0-%EB%B0%A9%EC%8B%9D-MCU-SFU-P2P
