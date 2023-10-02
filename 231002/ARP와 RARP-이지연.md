# ARP와 RARP
ARP(Address Resolution Protocol)와 RARP(Reverse Address Resolution Protocol)는 네트워크에서 사용되는 주소 결정 프로토콜입니다.

ARP는 IP 주소와 MAC 주소를 매핑하기 위한 프로토콜입니다. 
이더넷과 같은 로컬 네트워크에서 컴퓨터가 다른 컴퓨터로 데이터 패킷을 보내려고 할 때, 해당 컴퓨터의 IP 주소를 알아야 합니다. ARP는 이때 사용됩니다.

반면, RARP는 MAC 주소를 IP 주소로 변환하기 위한 프로토콜입니다. 
주로 컴퓨터가 자신의 IP 주소를 알아내려고 할 때 사용됩니다. 예를 들어, 컴퓨터가 부팅될 때 IP 주소를 자동으로 할당받아야 할 때 RARP가 사용됩니다.
(그러나 RARP는 현대 네트워크에서는 거의 사용되지 않고, DHCP와 같은 프로토콜로 대체되었습니다.)
