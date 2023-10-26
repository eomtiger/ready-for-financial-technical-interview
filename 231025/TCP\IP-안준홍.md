# TCP/IP
> 인터넷의 기본이 되는 프로토콜로 전송 제어 프로토콜(TCP: Transfer Control Protocol)과 인터넷 프로토콜(IP: Internet Protocol)을 의미합니다.

<br>

## 네트워크 접근 계층
- 운영체제의 네트워크 카드와 디바이스 드라이버 등과 같이 하드웨어적인 요소와 관련된 모든 것을 지원하는 계층입니다.
- 송신측 단말기는 인터넷 계층으로부터 전달받은 패킷에 물리적 주소인 MAC 주소 정보를 갖는 헤더를 추가하여 프레임을 만들어 전달합니다.

**대표 프로토콜**
- **이더넷(ethernet)**: 근거리통신망(LAN)의 대표적인 통신 프로토콜입니다.
- **MAC(Multiple Access Control)/LLC(Logical Link Control)**: IEEE 802 표준으로 규정하는 각종 연결 방식에서 공통으로 사용하는 통신 규약입니다.
- **SLIP(Serial Line Internet Protocol)**: IP에 대한 기본 프레임을 제공하는 매우 간단한 2계층 프로토콜입니다.
- **PPP(Point-to-Point Protocol)**: 프레임, 보안과 성능을 강화하기 위한 추가기능을 제공하는 프로토콜입니다.

<br>

## 인터넷 계층
- IP는 네트워크의 주소 체계를 관리하며, 데이터그램을 정의하고 전송을 위한 경로 결정을 담당합니다.

**대표 프로토콜**
- **IP(Internet Porotocol)**: 네트워크의 주소 체계를 관리하며, 데이터그램을 정의하고 전송을 위한 경로 결정을 담당합니다.
- **ARP(Adderess Resolution Protocol)**: IP주소를 MAC주소로 변환합니다.
-**RARP(Reverse ARP)**: MAC주소를 IP주소로 변환합니다.
- **ICMP(Internet Control Message Protocol)**: 에러 보고, 경로를 제어하는 정보 전달 기능이 있습니다.
- **IGMP(Internet Group Message Protocol)**: 멀티캐스팅 기능을 수행하는 프로토콜입니다.

<br>

## 전송 계층
- 네트워크 양단의 송수신 호스트 사이의 신뢰성 있는 전송 기능을 제공합니다.
- 시스템의 논리 주소와 포트를 가지므로 각 상위 계층의 프로세스를 연결합니다.

**대표 프로토콜**
- **TCP(Transfer Control Protocol)**: 전송되는 패킷에 에러가 없고, 보내진 순서대로 수신측이 받을 수 있도록 신뢰성 있는 데이터 전송을 보장합니다.
- **UDP(User Datagram Protocol)**: 패킷의 정확한 전송을 보장하지 않지만 빠른 전송이 필요한 경우 사용됩니다.

<br>

## 응용 계층
- 사용자에게 서비스를 제공해줍니다.

**대표 프로토콜**
- **FTP(File Transfer Protocol)**: 파일을 효과적으로 주고받을 수 있는 파일 전송 프로토콜로, 인터넷을 이용해 컴퓨터끼리 파일을 송수신할 수 있도록 지원하는 방법과 프로그램을 통칭합니다.
- **TFTP(Trivial File Transfer Protocol)**: FTP보다 더 단순한 방식으로 파일을 전송합니다. 데이터 전송 과정에서 데이터가 손실될 수 있는 단점을 갖지만 FTP처럼 복잡한 프로토콜을 사용하지 않기 때문에 구현이 간단합니다.
- **RTP(Real-time Transprot Protocol)**: 실시간으로 음성이나 통화를 송수신화기 위한 통신 규약입니다. 라우터 등의 단말기에 의지하지 않고 단말 간에 실행됩니다. UDP의 상위 통신 규약으로 이용되며, 타임스탬프를 근거로 지연이 큰 패킷을 포기할 수 있습니다.
- **HTTP(Hyper Text Transfer Protocol)**: 하이퍼텍스트 문서를 교환하는데 사용하는 통신 규약입니다. 웹에서 HTML 문서를 송수신하는 데 사용하며, 텍스트, 이미지, 멀티미디어 파일 등 다양한 형태의 데이터를 전소앟ㄹ 수 있습니다.
- **SMTP(Simple Mail Transfer Protocol)**: 네트워크의 두 메일 서버 사이에서 이메일을 송신하는데 사용하는 프로토콜입니다.
- **POP3(Post Office Protocol3)**: 이메일을 수신하기 위한 표준 프로토콜입니다.
- **IMAP(Internet Mail Access Protocol)**: 메일을 저장하는 복사하는 프로토콜로, 메일 수신에 사용됩니다.
- **Telnet(Telecommunication Network Protocol)**: 원격지에서 컴퓨터를 이용한 가상 단말 기능을 구현하는 프로토콜입니다. 원격지에 위치한 호스트 컴퓨터를 로컬 컴퓨터처럼 사용할 수 있습니다.
- **SNMP(Simple Network Management Protocol)**: 다른 네트워크 장치를 원격에서 관리하기 위한 간단한 방법을 제공하는 인터넷 표준 프로토콜입니다.
- **DHCP(Dynamic Host Configuration Protocol)**: 네트워크의 각 노드들에게 유일한 IP주소를 자동으로 할당해주고 관리해주는 프로토콜입니다.
- **DNS(Domain Name System)**: 호스트의 이름과 IP주소를 매핑하여 주는 분산 네이밍 시스템입니다. 덕분에 사용자는 숫자로 구성된 IP주소 대신 호스트의 이름을 기억하면 됩니다.

<br>

---

### 참조
- 컴퓨터일반(박미진)

