# route_53
#Route 53

* 도메인 구매 대행 업체이다. 구매 대행자는 top level domain을 기반으로 관리하는 기관이 모두 다르다. 따라서 그걸 담당하는 등록소 registry라고 부르는 곳에 등록자가 사려고 하는 DNS를 살 수 있는지 등록 대행자를 통해서 등록소에서 구매해야한다.

* 도메인을 구매했으면, 그 domain에 IP를 연결해야한다.
* PC를 통해서 내가 직접 server를 장만해도 되지만 route 53같은 것이 이런 일을 대신해서 해준다. ( 나에게 DNS를 임대해주는 것 )
* 장만이 완료되면 example.com의 주소는 93.184~이다.
* 세팅이 완료되면 .com의 registry에게 example.com의 DNS를 관리하는 Domain name server가 a.iana-servers.net라는 것을 알려줘야 한다. ( 이것을 등록 대행자가 등록소에게 example.com에 대한 정보는  a.iana에 저장되 었다 라고 알려주면 등록소가 갖고 있는 Domain name server에 example.co의 name server는 a.aian~이다라고 기록해 두면 등록 과정이 끝나게 된다.) -> domain과 ip를 매칭하는 작업이 끝나게된다.  만약에 IP주소가 변경되었따 해도 ip 주소만 바꾸면 될만큼 편해진다

##Client 

입장Client는 인터넷에 연결하기 위해 랜선이나 와이파이에 연결하는 순간에 사업자 (ISP)에 의해서 컴퓨터가 사용할 DNS를 자동으로 setting 해준다. 예를 들어 1.1.1.1이라는 DNS가 setting 되었다고 가정하고 수업을 진행하자. 이 후 client는 domain에 접속하기 위해 IP를 알아내기 위해 이 때 설정된 DNS를 이용하게된다.

<span style ="color:blue">맨처음 Domain name 주소를 맨 먼저 root name server에 물어보게 된다. root name server가 누군지는 모든  name server에 적혀있다.**( 상수로 박혀있다.)** root name server에 example.com의 주소가 어디야? 물어보면 root name server는 알지 못한다 하지만, .com이라는 등록소가 어떤 name server에서 운영되는지는 알 고 있다. 그래서 그러한 name server인 (a.gtld~ 에게 물어보라고 DNS에게 알려주게 된다.) 그러면 DNS Server는 다시 a.gtld~에게  example.com의 IP에 대해 물어본다. 하지만 또 모른다( 그 대신에, example.com의 name server가 a.iana~ 이다 라는 것을 알려준다.) 우리의 DNS server는 a.iana에 접속해서  example.com의 ip가 뭔지 또 물어보면 이 때 93.184~ 라는 client에게 그 IP를 알려주게 되면서 과정이 끝나고 해당 주소로 접속할 수 있게 되는 것이다.</span>

<span style = "color:red">이러한 긴 과정에서  route 53의 핵심기능은 등록 대행자로서의 기능과, name server를 임대해주는 역할을 하는 것이다.</span>

