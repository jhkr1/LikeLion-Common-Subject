# Like Lion 공통 과제

## Web의 등장

- PC의 보급이 바로 인터넷으로 이루어지진 않았다. 게임, 문서등의 CD가 대중적이었다.
- 1990~2000초 ⇒ 초고속 인터넷망 보급, 이전에도 PC통신이 있었지만 인터넷선이 아니라 전화선을 사용했다. 다른사업자 간에 통신이 불가했다.
- 팀 버너스리가 wwWeb을 만들어냄.

  |PC통신|Web|
  |-------|------|
  |폐쇄|개방|
  |저속|고속|
  |전화선/모뎀|광랜(FTTH)|
  1. Web1.0 1990후반 ~ 2000년대 ⇒ 어느 누구나 프로그램을 대중에게 공개할 수 있는 세상 도래. 메신저, 쇼핑몰 사이트등의 인기를 가져옴.
  2. Web2.0 2010년대 ~ 현재 ⇒ 일방향적으로 정보를 제공받던 사용자. 직접 정보를 생산하고 공유. 스마트폰의 시대로 더욱 확장됨. SNS의 인기.
  3. Web3.0 ⇒ 현재도 발전 중임. 현재 과도기를 거치고 있고 데이터의 투명한 공개를 메인으로함.(블록체인) 느린 네트워크 처리 속도. 책임 소재가 불분명함.
<hr/>
## 클라이언트와 서버

- 웹브라우저를 사용함 ⇒ 크롬, 사파리 브라우저가 대표적 예시
- 브라우저의 도움을 반드시 받아야한다.
- 클라이언트(요청을 보내는 주체)(Request)
- 서버(응답을 보내는 주체)(Response)
<hr/>
## HTTP 통신과 URL

### HTTP(HyperText Transfer Protocol)

- 통신을 하기위해서는 규칙이 필요함.
- HyperText ⇒ 링크 || Protocol ⇒ 규칙

### URL(Uniform Resource Locator)

#### http://www.google.com/search?/techit을 예시로 들어보자

1. http:// ⇒ 프로토콜(통신규칙)
2. www.google.com ⇒ 호스트(서버의 주소)
3. /search ⇒ 경로(호스트 내 서비스의 위치)
4. ?/techit ⇒ 쿼리 문자열(?기호로 시작, &로연결, 키/값 쌍으로 구성)
<hr/>
## 세션, 쿠키, 토큰

### 쿠키
- 브라우저에 데이터 저장 => Response에 쿠키가 있다.
- 도메인에 따라 제한됨
- 유효기간이 있음.
- 인증 뿐만 아니라 다른 정보를 저장할 수 있음
### 세션
- 요청끼리 연결,메모리가 없음.
- 세션에 별도의 ID가 있고 쿠키를 통해 브라우저로 돌아오고 저장된다.
- 다른 페이지로 넘어갈 때마다 세션ID를 갖고있는 쿠키를 서버에 보낸다.
- 해당 세션ID를 가지고 세션DB를 확인하고 그때서야 서버가 ID를 확인할 수 있다.
- 이 모든것이 계속 반복된다.
- 유저가 갖고있는 것은 세션뿐이고 쿠키는 전달하기위한 매개체일 뿐이다.
- 모든정보를 저장해 새로운 기능 추가 가능. ⇒ DB가 있기때문에가능. 때문에 돈도 많이들어간다.(인스타그램)
### 토큰
- 쿠키가 없는 native에 토큰을 사용한다. 
- req마다 쿠키를 받아 세션 ID를 보고 DB에서 일치하는 유저를 찾아야 진행이 가능하다.
- JWT라는 토큰 형식이 이때 등장하고, 세션 DB가 필요없다.
### JWT
- JWT는 보통 세션ID보다 길다.(제약 X), 사인된 정보를 서버에 보낸다.
- JWT는 유저인증정보를 토큰에 저장한다. 토큰이 유효한지 검증만하면 되기에 DB를 거치지 않는다.
- 암호화 X ⇒ 누구나 열람 가능하다 ⇒ 때문에 비밀번호는 맞지않.
- 토큰의 유효 정보만 검사한다. DB가 필요없음. 유효성 검증에 특화.(QR 코드)
<hr/>
## IP, Port , DNS

### 네트워크
- 2개 이상의 컴퓨터가 연결된 통신망
- 어떻게 데이터가 오가는지 이해하는 것이 핵심이다.
1. 스위치 ⇒ 동일한 네트워크 안에서 호스트가 가능하게 하는 역할. 다른 네트워크에는 접속할 수 없다.
2. 라우터 ⇒ 스위치를 보완하기 위해 출현. 서로 다른 네트워크 간에 통신이 가능하다.(공유기라고도 부름)
### IP(Internet Protocol)
- 컴퓨터 간 데이터를 주고받는 네트워크 계층의 규약, 데이터 전달에 필요한 목적지 컴퓨터 정보가 필요하다.
- 1100000/10101000/00000000/00000011 ⇒ 4등분 하여 각각을 옥텟이라고 한다.(0.0.0.0 ~ 255.255.255.255)
- (ISP → 공인IP → 사설IP)
1. 공인 IP(Public IP) ⇒ 전체 인터넷 망에서 고유하게 식별 가능한 주소, IPv4체계에서 자원 부족. 하나의 공인 IP에서 수많은 사설 IP 할당이 가능하다.
2. 사설IP(Private IP) ⇒ 가정의 LAN과 같은 네트워크에서 할당되는 주소. 내 IP는 보안 때문에 공개되지않고 외부 IP의 형태로 보여진다.
- 127.0.0.1 ⇒ 특수한 IP 주소 ⇒ 이는 자기 자신을 가리키기위한 약속된 주소(localhost)이다.
### Port
- 서비스의 최종 목적지를 정해줘야함. 서비스를 구분하는 역할을 한다. 번호는 application 종류에 따라 다르다.
- HTTP ⇒80, HTTPS ⇒443, SMTP ⇒25, FTP⇒21
- 접근하려는 서비스의 목적지 포트를 정확하게 설정해야한다.
### DNS(Domain Nave Server)
- URL을 해석하여 IP 주소로 반환하는 서버
- 매칭되는 정보를 찾는다. ⇒ IP정보를 브라우저로 보낸다.
- 전세계 DNS는 연결되어 있다.
- 클라이언트가 서비스를 이용하고자하는 관문과 같다. 장애 발생 시 각종 서비스들에 접근할 수 없다.

