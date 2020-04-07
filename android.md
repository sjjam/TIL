## 3/23

안드로이드 설치

https://developer.android.com/

![image-20200323091706188](images/image-20200323091706188.png)

개발할때 버전을 맞출 수 있다.



## 4/6

xml  안올라 올때

clean project  > rebuid project > build.gradle 두개 > sync하고 재실행



## 4/7

### 사용자 정의 Adapter 만들기

- 안드로이드에서 앱을 구성할때 목록형식을 가장 많이 사용

- 사용자정의로 디자인한 뷰를 목록으로 사용하고 싶은 경우

- 안드로이드 내부에서 제공하는 Adapter로 표현하고 싶은 내용을 

  모두 표현할 수 없다.(이벤트연결, 각 목록의 구성을 다르게 생성...)

### [구성요소]

- Adapter를 이용해서 출력할 데이터를 저장하는 객체(DTO)

- 사용자정의 Adapter

  1) 안드로이드에서 제공하는 Adapter클래스를 상속

  - 리스트뷰를 만들때 필요한 정보를 저장할 수 있도록 멤버변수 정의(Context, row디자인 리소스, 데이터)

  2) 생성자 정의

  - 상속받고 있는 ArrayAdapter의 생성자 호출

  3) ArrayAdapter에 정의되어 있는 메소드를 오버라이딩

  - getView : 리스트뷰의 한 항목이 만들어질때마다 호출

    => 전달된 리소스를 이용해서 뷰르 생성(LayoutInflator)

    => 한 row를 구성하는 뷰를 찾아서 데이터와 연결

  4) getView메소드에서 성능개선을 위한 코드를 작성

  - 한 번 생성한 view를 재사용
  - findViewById는 한 번만 찾아오기

  5) ViewHolder 객체를 생성

  - row를 구성하는 뷰를 한 번 findViewById하기
  - row에 대한 구성 View를 멤버변수로 선언
  - 생성자에서 findViewById처리를 구현
  - 최초로 뷰를 만들때(row에 대한 뷰) 이 객체를 활용

  6) row를 구성하는 뷰에 상태값을 저장하기

  - 각 뷰의 이벤트를 통해 저장

  - 각 뷰의 상태값을 저장할 수 있도록 객체

    : 상태값을 저장한 객체를 자료 구조에 저장

      focus를 잃어버릴때 상태를 저장

- Adapter를 통해 만들어진 리스트뷰를 보여줄 액티비티

  - main layout필요