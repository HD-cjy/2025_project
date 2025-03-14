# 기본 필드 변수 private으로 선언

public Member() { }<< 기본 생성자 생성

![[Pasted image 20250310142835.png]]

기본 Getter,Setter 설정완료하기.


```java - controller
// - mem
 private Member mem = new Member("admin","1234","홍길동","901202-1582321",163.0);

public MemberController(){

}
public int login(String id, String pwd){

	return 0;
}
public Member readInfo(){
	retrun null;
}
public int readAge(){
	return 0;
}
public void updateHeight(double height){

}```

```java
System.out.println("아이디 입력:");
String id = sc.nextLine();
System.out.println("비밀번호 입력:");
String pwd = sc.nextLine();

int result = mc.login(id,pwd);

if(result == 1){

	while(true){
		System.out.println("==== 회원 프로그램 ====");
		System.out.println("1. 내 정보 보기");
		System.out.println("2. 내 나이 조회하기");
		System.out.println("3. 키 수정하기");
		System.out.println("9. 프로그램 종료하기");
		System.out.println("메인 번호 선택)");
		int num = sc.nextInt();
		sc.nextLine();
		switch(num){
		case 1: mc.readInfo(); break;
		case 2: mc.readAge(); 
		if(age!=0){
		Sysout.("내 나이는"+age+"살 입니다.");
		}else {
		Sysout.("주민번호 입력이 올바르지 않습니다. 확인 요망.");
		}
		break;
		case 3:updateHeight(); break;
		case 9:Sysout.println("프로그램 종료"); return;
			default : System.out.println("잘못입력하셨습니다");
	
	}
	}
}
else{//로그인 실패경우.
	System.out.println("프로그램 종료!"); return;
}
```

```java
public int login(String id, String pwd){
//전달받은 아이디, 비밀번호 저장되어있는 mem의 아이디 비밀번호가 같은지 확인
	if(id,equals(mem.getMemberId()) && pwd.equals(mem.getMemberPwd())){
		return 1;
	}
	return 0;
}
```

//mem의 주소값을 반환하는 메서드.
화면에 mem 의 정보를 출력하고자 한다면
mem. 즉 Member클래스에 정의한 infomation() 메소드ㅇ를 호출하여 
정보 문자열을 print문에 담아서 출력하면 된다.

##### 비교대상이 null 이 나올 수 있으면 Null이 뒤쪽으로 오게끔 처리 해야한다.
###### 앞쪽에 널이 들어오면, 널을 참조하려 해서 오류 토해냄.



## substring(index)
### substring(sart index)
-  시작 인덱스를 기준으로 잘라서 반환
### substring(sart index , end index)
- 인덱스의 번호로 내가 원하는 곳을 조절하여 자를 수 있음.
- 단, 끝인덱스는 __-1 문자까지만 출력__ 해줌


## Integer.Parseint(문자열);
int y = Integer.parseInt(year); ::: 참조 자료형. ( 문자를 숫자로 변환해주는 메소드다.)

```java
int age = 0; //최종 나이를 담을 변수
int year = Integer.parseInt(citizenYear); //추출한 년도를 숫자로 변환.
age = 2025 - year +1;
```



```java
//업데이트 하는 법 : 세터 메서드 사용으로 업데이트 하기
Sysout("키 입력");
double height = sc.nextDouble();
sc.nextLine();

mc.updateHeight(heifgt); //멤버 컨트롤러에 있는 updateHeight
```


# 복습 : 객체를 만드는 이유
- 속성이나 특징들을 이용하여 클래스(자료형) 을 묶는 것. 
- 여러가지 자료형을 한데 묶어서 관리할 수 있음. === 그걸 해줄 수 있는 것이 클래스 자료형임.
- 값을 담는 객체 (VO= Value Object)
## 생성자
- 뽑아내고 싶은 객체에 사용할. 객체의 영역을 할당시켜주는 구문 
- 기본 생성자 `public Member(){}` ==>> heap에는 빈 공간이 있을 수 없으니까 기본값이라도 넣어놓자.

- 매개변수가 있는 생성자.==> 
  전달값이 있는 생성자. ( 전부 정해져 있음.)

- 생성자는 무엇도 반환하지 않음 (= 왜냐하면 초기화 선언문이기 때문에.);

### 매개변수 생성자는 이미 전달받을 값을 알고 있을때, 객체를 생성하기 용이.

## 메소드 오버로딩 
- 메소드 오버로딩 상황이 아니라면 생성자의 이름은 같을 수 없다. 
- 메소드 오버로딩 

## 필드에 전달 받은 값을 대입해주기.
#### this.변수명 = 변수명;
전달받은 변수값을 필드에 대입하기 위한 키워드 **this**
==> 주소값을 전달받는다.


## 객체, 즉 내가 뽑아낸 애들이 여러 변수를 가지고 있으니까
그걸 형식 (설계도 = 필드 )로 묶어서 하나의 자료형으로 선언해준거임.
자료형으로 메모리영역에 할당을 받으려면 
class 별칭 = new 생성자 명();  으로 할당을 받음.
그럼 기본 생성자가 있어야함. 그래야 heap 메모리에 기본값을 대입해줌. (메모리영역에 미리 자리를 맡아주는 것이 기본 생성자. )
내가 전달할 값이 정해져 있으면 매개변수 생성자를 정의하고 사용하면 됨.
정의를 해야 사용 할 수 있음.

매개변수 생성자가 하나도 없으면, JVM이 자동으로 생성해줌.
매개변수 생성자 : 내가 필요한 생성자가 있을때.! 

## 정의 구문 과 생성구분의 차이
정의 구문이 있어서 생성구문을 사용 가능

## Getter와 Setter
### 필요성
- 필드에 직접접근을 시키지 못하게 하기 위해. (기본 캡슐화 원칙임.)
- 접근제한자를 사용하여 정보은닉을 위해 private로 만들어서 
  
  
  1.  값을 가져오는, 얻어오는 getter
```java
public void setName(String name) {
		this.name = name;
	}
```
setter는 void 즉 반환할 값이 없으므로 void 

2. 값을 설정하는, Setter 
```java
public String getName() {
		return name;
	}
```
![[Pasted image 20250310174523.png]]