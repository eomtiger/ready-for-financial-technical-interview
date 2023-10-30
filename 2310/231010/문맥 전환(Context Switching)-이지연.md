# 문맥 전환(Context Switching)이란?

멀티 프로세스 환경에서 CPU가 어떤 하나의 프로세스를 실행하고 있는 상태에서 **인터럽트 요청에 의해** 다음 우선 순위의 프로세스가 실행되어야 할 때 **기존의 프로세스의 상태 또는 레지스터 값(context)을 저장**하고 CPU가 다음 프로세스를 수행하도록 **새로운 프로세스의 상태 또는 레지스터 값(context)을 교체하는 작업을 context switching**이라고 합니다.

*OS에서 context는 CPU가 해당 프로세스를 실행하기 위한 해당 프로세스의 정보들이다.
*보통 context는 프로세스의 PCB(Process Control Block)에 저장된다.
