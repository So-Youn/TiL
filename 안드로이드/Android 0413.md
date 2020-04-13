# [ 구글 라이브러리](https://console.developers.google.com/apis/library?hl=ko&supportedpurview=project)

## Map

![image-20200413093805323](images/image-20200413093805323.png)

<img src="images/image-20200413094047588.png" alt="image-20200413094047588" style="zoom:80%;" />

![image-20200413094249512](images/image-20200413094249512.png)

* market에서는 어플을 패키지명으로 구분한다.

  * 따라서, package명과 인증서 명을 등록해주어야 한다.

*  play service 등록해 주어야 한다.

  * version 확인

    ![image-20200413095020522](images/image-20200413095020522.png)

  * SDK Tool

    ![image-20200413095103004](images/image-20200413095103004.png)

  * ![image-20200413100626835](images/image-20200413100626835.png)

    * pom.xml 과 같은 기능
    * sync now를 눌러 다운로드 받는다.

    <img src="images/image-20200413100856032.png" alt="image-20200413100856032" style="zoom:67%;" />

* dependancy 목록 확인

<img src="images/image-20200413094657284.png" alt="image-20200413094657284" style="zoom:80%;" />

![image-20200413101136635](images/image-20200413101136635.png)



![image-20200413101409207](images/image-20200413101409207.png)

* interner에서 google지도를 받아올 것이므로 permission이 잇어야 한다.

  <img src="images/image-20200413101727612.png" alt="image-20200413101727612" style="zoom:80%;" />

[결과]

<img src="images/image-20200413101955970.png" alt="image-20200413101955970" style="zoom:80%;" />

### 위치 정보 가져오는 방법 (1)

* 표준방법인 LocationManager를 통해 가져오기
  * 위치정보를 제공하는 객체의 종류와 현재 사용할 수 있는 위치정보 제공자를 확인
* 오류상황 - AVD에서 gps모듈을 제공하지 않는다.





>  위치정보를 제공하는 제공자로부터 위치정보를 담고 있는 Location객체를 가져오기 
>
> ACCESS_FINE_LOCATION : GPS
>
> ACCESS_COARSE_LOCATION: NETWORK

![image-20200413134930365](images/image-20200413134930365.png)

![image-20200413135021362](images/image-20200413135021362.png)

### (2)

다른 `provider`정보를 확인하고 사용할 수 있도록 작업

* `gps`, `network` 모듈을 함께 호출해서 먼저 받아지는 Provider를 이용해서 작업할 수 잇도록 구현

```java
    List<String> provider_list ; //전체 위치 제공자 목록
    List<String> enableProvider_list; // 사용가능한
```

![image-20200413135241376](images/image-20200413135241376.png)

![image-20200413164901691](images/image-20200413164901691.png)

* 지도 활용
  * override 

![image-20200413141357664](images/image-20200413141357664.png)

* [google 지도](https://www.google.com/maps/d/edit?hl=ko&hl=ko&mid=1-omrjOaLzLCMyBoi4K01cInUYDR1S394&ll=38.79725058767069%2C125.38974110451045&z=7)

![image-20200413144305331](images/image-20200413144305331.png)

* import

![image-20200413144332906](images/image-20200413144332906.png)

## Fragment

> 화면의 **일부분**만 다른 화면으로 구성하고 싶을 때
>
> 하나의 화면을여러 부분으로 나눠서 보여주거나, 각각의 부분 화면 단위로 바궈서 보여주고 싶을 때 
>
> 분할된 화면을 **독립적**으로 구성하고 그 상태를 관리
>
> fragment는 항상 Activity 위에 있어야 한다.

* FrameLayout 시 Activity 가 많아지면 메모리를 많이 차지하기 때문에 fragment를 이용해서 작업해준다.
* 페이지를 쌓아 놓는 것이 아니라 교체를 하는 것.

* fragment는 name을 꼭 설정해주어야 한다.

### [예시]

* 화면에 연결할 프레그먼트 객체를 생성한다.

![image-20200413163622749](images/image-20200413163622749.png)

* **FragmentManager** getFragmentManager()
  * 프래그먼트를 폼함하는 Activity에서 프래그먼트 객체들과 의사소통하는 FragmentManager 반환
  * FragmentManager 객체는 프래그먼트를 액티비티에 추가, replace, 삭제할 때 주로 사용
  * `getSupportFragmentManager` 와 ` getFragmentManager()`는 같다.
    * `getSupportFragmentManager` 가 이전 버전과 호환됨 - 권장.
* **FragmentTransaction** beginTransaction()
  * 프래그먼트를 변경하기 위한 트랜잭션 시작.

![image-20200413163652473](images/image-20200413163652473.png)

<img src="images/image-20200413164513533.png" alt="image-20200413164513533" style="zoom:80%;" />



* fragment 에는 setContentView() 메서드가 없다.
  *  인플레이션 객체인 **LayoutInflater**를 이용해 인플레이션 진행
  * xml 레이아웃 파일의 내용을 인플레이션 후, 클래스에서 사용하도록 하는 메서드 `onCreateView()`
  * 인플레이션이 끝나면 프래그먼트가 하나의 뷰처럼 동작.

![image-20200413163909754](images/image-20200413163909754.png)

* fragment는 뷰와 달라서 뷰를 담고있는 **공간**만 확보한다.
  * xml에 fragment를 추가하면 동적(코드)로 제어가 어렵다.

![image-20200413164646286](images/image-20200413164646286.png)

* FrameLayout - fragment 
  * Activity로 나눈 뒤 조각 코드 식으로 붙여 넣는다.

![image-20200413171630672](images/image-20200413171630672.png)

![image-20200413172006109](images/image-20200413172006109.png)