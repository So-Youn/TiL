## 1. Drawable

* 뷰에 설정할 수 있는 객체이며, 그 위에 그래픽을 그릴 수 있다.
* 드로어블 XML 파일은 이미지를 버튼 배경으로 설정한 것처럼 `/app/res/drawable` 폴더 안에 넣어 버튼(뷰)의 배경으로 설정

![image-20200327092350360](images/image-20200327092350360.png)

* ![image-20200327092626502](images/image-20200327092626502.png)

<img src="images/image-20200327094846407.png" alt="image-20200327094846407" style="zoom:67%;" />

![image-20200327094929416](images/image-20200327094929416.png)

##  

**안드로이드는 API 레벨 별로 이용할 수 있는 클래스와 메서드가 다르다.** 

안드로이드의 정적 메소드 이용해서 텍스트 작성 

![image-20200327101753911](images/image-20200327101753911.png)

![image-20200327101739331](images/image-20200327101739331.png)



![image-20200327102210274](images/image-20200327102210274.png)











![image-20200327104448334](images/image-20200327104448334.png)

### 채팅창 만들기

* LinearLayout  지정해주기.



![image-20200327113823491](images/image-20200327113823491.png)

* AVD에 에러가 생길 때

![image-20200327145613162](images/image-20200327145613162.png)

![image-20200327145648341](images/image-20200327145648341.png)

* 데이터 초기화

![image-20200327145700413](images/image-20200327145700413.png)

## 2. ETC - event 처리

* `Activity`는 화면이라고 생각
* Activity1 에서 Activity2화면 변경 할 때 new 해서 하지 않고 **component 기반**으로 연동
* 모든 activity 는 Manifest에 저장되어야 한다.
* `<intent-filter>`가 가장 먼저 실행되는 것.

### 1. SeekBar

* 설정을 나타낼 때
* 사용자가 값 변경이 가능하다.

![image-20200406094313693](images/image-20200406094313693.png)

![image-20200406094222004](images/image-20200406094222004.png)

* AppCompat : 호환성

![image-20200406094917453](images/image-20200406094917453.png)

* layoutXml

<img src="images/image-20200406095302069.png" alt="image-20200406095302069" style="zoom:80%;" />

[결과]

![image-20200406095123366](images/image-20200406095123366.png)

* 버튼으로 설정 값 변경하기

![image-20200406103319844](images/image-20200406103319844.png)

<img src="images/image-20200406103526779.png" alt="image-20200406103526779" style="zoom:80%;" />

* 리스너 연결

![image-20200406103640014](images/image-20200406103640014.png)

![image-20200406110507294](images/image-20200406110507294.png)



* 모든` id`는 int형 상수
  * ![image-20200406111614850](images/image-20200406111614850.png)
* SeekBar 값 불러와서 setting 하기



![image-20200406104554232](images/image-20200406104554232.png)

* touch 처리
  * web의 keypress up/down 과 비슷

![image-20200406111024118](images/image-20200406111024118.png)

### 2. ProgressBar

* 진행 상황을 나타내준다.
* `read-only` - 사용자가 수정이 불가능하다.

<img src="images/image-20200406095411243.png" alt="image-20200406095411243" style="zoom:80%;" />

![image-20200406095606730](images/image-20200406095606730.png)

![image-20200406101118814](images/image-20200406101118814.png)

*  ProgressBar 증가/감소/설정시키는 버튼 만들기

![image-20200406101716388](images/image-20200406101716388.png)

<img src="images/image-20200406102511125.png" alt="image-20200406102511125" style="zoom:80%;" />

![image-20200406101748005](images/image-20200406101748005.png)

* 만약 0~100부터 증가시키고 싶으면 for문을 돌려서 동작시키면 된다.

### 3.  [etc](https://developer.android.com/guide/components/activities/intro-activities)

* DatePicker

![image-20200406112228444](images/image-20200406112228444.png)

* CalendarView

![image-20200406112135352](images/image-20200406112135352.png)

#### Layout 인식 에러 발생시

<img src="images/image-20200406111745964.png" alt="image-20200406111745964" style="zoom:50%;" />

![image-20200406111857803](images/image-20200406111857803.png)

* gradle이랑 sync 맞춰주기

<img src="images/image-20200406111451051.png" alt="image-20200406111451051" style="zoom:80%;" />