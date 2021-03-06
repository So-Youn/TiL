## :star: Android View

> View : 일반적으로 컨트롤이나 위젯으로 불리는 UI  구성 요소.
>
> ​				즉, 사용자의 눈에 보이는 화면의 구성 요소들. 
>
> ViewGroup 은 뷰를 상속하여 뷰그룹도 뷰처럼 다룰 수 있다.

* **View** :mobile_phone_off: : 화면을 디자인하는 구성 요소  *(ex, 버튼, 텍스트 .. )*
  
  ​	흔히 콘트롤이나 위젯이라고 불리는 UI 구성요소
  
  * **ViewGroup** : View를 여러 개 담고 있는 모음
    * 뷰 그룹도 뷰에서 상속하여 뷰가 된다. 
    * Layout : View를 어떻게 배치할 지 
  * **Widget** : 일반적인 컨트롤의 역할을 하고 있는 것
    * TextView
    * Button<img src="images/image-20200325154708232.png" alt="image-20200325154708232" style="zoom:80%;" />

* **Layout** : 뷰 그룹 중에서 내부에 뷰들을 포함하고 있으면서 그것들을 배치하는 역할.

* 액티비티의 상속

  * 처음 만들어 본 액티비티에서 extends 키워드 사용

  ```java
  public class MainActivity extends AppCompatActivity
      //MainActivity : 내가 만든 액티비티
  ```

### 1. widget :phone:

* 화면을 디자인 할 때는 Layout객체 위에 view를 올려놓아야 한다
  * `ConstraintLayout` : 기본 레이아웃

<img src="images/image-20200325093543372.png" alt="image-20200325093543372" style="zoom:50%;" />

* LinearLayout : 순서대로 배치되는 것.
  * **Layout_width** : View의 너비
  * **Layout_height** : View의 높이
    * **Layout_width** 와 **Layout_height** 는 반드시 있어야 한다.
  * **orientation** : 배치 방향
  * **id** : 각 위젯을 식별할 수 있는 이름
  * **margin** : 주위 여백
  * **padding** : 내부 컨텐츠와 border 사이의 간격
  * **layout_weight** : 여백을 해당 view의 사이즈로 포함
  * **Layout_gravity** : parent 내부에서 View의 정렬
  * **gravity** : view 내부에서의 정렬 *(ex . 글자 정렬)*
* android:layoutXXX : 지정한 영역만 보여준다
  * **match_parent** : 뷰 그룹에 남아있는 여유 공간을 꽉 채운다
    * 부모의 width 사이즈만큼 그린다. 
  * **wrap_content** :  뷰에 들어있는 내용물의 크기에 따라 크기 결정된다. 
    * 원래 가지고 있는 정 사이즈
  * 크기 값 지정 : `dp`(버튼) , `px`,`sp` (글자)

![image-20200325093744162](images/image-20200325093744162.png)

![image-20200325094129383](images/image-20200325094129383.png)

* orientation = " vertical "

![image-20200325094553451](images/image-20200325094553451.png)

* 버튼 3개의 너비와 높이가 부모에 맞게 꽉 차게 그려져서 1개만 나온다.

![image-20200325094909734](images/image-20200325094909734.png)

![image-20200325094947226](images/image-20200325094947226.png)

* activity (xml) 파일 **rename** 방법 : refactor

![image-20200325095234922](images/image-20200325095234922.png)

![image-20200325095355209](images/image-20200325095355209.png)

![image-20200325095544228](images/image-20200325095544228.png)

![image-20200325095434877](images/image-20200325095434877.png)

* id  설정 : 식별성을 주기 위한 속성 

![image-20200325101713892](images/image-20200325101713892.png)

* 버튼 사이즈 설정 - `dp`라는 단위를 지정해주어야 한다.   - `dip` 의미
  * `dp`를 사용하게 되면 다른 크기의 diplay에서 깨질 수 있다. 
  * 웬만하면 match 와 wrap 이용하기

![image-20200325101933767](images/image-20200325101933767.png)

* padding 설정

![image-20200325102921071](images/image-20200325102921071.png)

* layout_weight

  * 만약 1로 설정 시 여백을 전체 다 차지한다. 
  * 전체 다 1로 설정 시 ( 1: 1: 1)

  ![image-20200325103307177](images/image-20200325103307177.png)

  * 2: 1: 1 로 설정시 ![image-20200325103407973](images/image-20200325103407973.png)

* Layout_gravity

![image-20200325103914763](images/image-20200325103914763.png)

* gravity

![image-20200325104123143](images/image-20200325104123143.png)

###  2. 레이아웃 추가

![image-20200325104348801](images/image-20200325104348801.png)

* TextView : 기능 없이 그냥 보여지는 글자 
  * 글자 없이 wrap_content 만 잡힌 상태

![image-20200325105058834](images/image-20200325105058834.png)

![image-20200325114414656](images/image-20200325114414656.png)

![image-20200325114358881](images/image-20200325114358881.png)

* 하나의 화면에 여러개의 레이아웃 중첩하기

  * 전체 outer : vertical
  * 내부 : horizontal
  * 버튼은 무조건 wrap...

  ```xml
   <Button
              android:layout_width="wrap_content"
              android:layout_height="wrap_content"
              android:text="버튼3"/>
  ```

  ![image-20200325115123437](images/image-20200325115123437.png)

  

<img src="images/image-20200325131726530.png" alt="image-20200325131726530" style="zoom:80%;" />

* MainActivity에 layout이 올라오지 않을 경우

* <img src="images/image-20200325133932919.png" alt="image-20200325133932919" style="zoom:80%;" />

### 3. Constraint

* `RelativeLayout `: 상대적으로 상위 컴포넌트
  * 이웃 컴포넌트의 위치를 가지고 상대적으로 배치시키는 것 
  * 규칙(Rule)기반 모델
* `Constraint_Layout` : 제약사항 ( 왼쪽, 위쪽 )을 주어 위치를 지정해준다
  * 기준이 되는 뷰 (Parent xxx) 를 잡아놓고 그에 따라 움직인다.
    * 이동 시 같이 이동된다. 
    * 연결 선을 만들어주어야 한다.

![image-20200325134701512](images/image-20200325134701512.png)

* 제약 조건(연결 선)은 앵크 포인트, 크기는 핸들을 통해서 조정한다.

<img src="images/image-20200402163426824.png" alt="image-20200402163426824" style="zoom:80%;" />

* 연결 선 자동 생성

![image-20200402162017803](images/image-20200402162017803.png)

* **연결 선** ?
  * 부모 레이아웃이나 다른 뷰와 연결 가능하다. 

![image-20200325135239424](images/image-20200325135239424.png)

* 좌 우로 연결해주면 정중앙에 위치한다.

<img src="images/image-20200402162514838.png" alt="image-20200402162514838" style="zoom:67%;" />

* bias를 이용해서 위치 조정하기

<img src="images/image-20200402162853438.png" alt="image-20200402162853438" style="zoom:67%;" />

* **기준 선**(guide line) 만들기
  * 정렬을 좀 더 쉽게 만들어 준다.

<img src="images/image-20200325142021714.png" alt="image-20200325142021714" style="zoom:80%;" />

<img src="images/image-20200402163031894.png" alt="image-20200402163031894" style="zoom:67%;" />

* 첫번째 실행되는 Activity임을 나타내는 구간

![image-20200325145145547](images/image-20200325145145547.png)

* gradle: build tool
  * 컴퓨터가 알아들을 수 있는 형태의 format으로 변경해준다.

![image-20200325151029575](images/image-20200325151029575.png)

* ![image-20200325165301108](images/image-20200325165301108.png)
  * Activity 수정

![image-20200325165326323](images/image-20200325165326323.png)

![image-20200325165142492](images/image-20200325165142492.png)

![image-20200325165228160](images/image-20200325165228160.png)

* android:id 

  ![image-20200325172552289](images/image-20200325172552289.png)

  * @id: 식별자 
  * @android : 내부에서 제공해주는 식별 값 참조해서 쓸 때 
  * @app : 외부 library / 직접 만든 속성

* 런쳐 갯수만큼 생성

<img src="images/image-20200325173120948.png" alt="image-20200325173120948" style="zoom:50%;" />

### 4. Button 복습

* Intent 를 이용해서 버튼 실행시키기 *(MainActivity)*

<img src="images/image-20200328004859594.png" alt="image-20200328004859594" style="zoom:80%;" />

<img src="images/image-20200328004924453.png" alt="image-20200328004924453" style="zoom: 50%;" />

* layout이동 *( MenuActivity )*

<img src="images/image-20200328005045651.png" alt="image-20200328005045651" style="zoom:80%;" />

<img src="images/image-20200328005118385.png" alt="image-20200328005118385" style="zoom: 67%;" />

* 메소드 override

<img src="images/image-20200401213311918.png" alt="image-20200401213311918" style="zoom: 67%;" />

* 파일의 내용 검색 : Find in path
  * 검색하고 싶은 단어 입력 

![image-20200401213453669](images/image-20200401213453669.png)

