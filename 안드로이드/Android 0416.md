# 머티리얼 디자인

* 플랫폼 및 기기 전반의 시각적 요소, 움직임 및 상호작용 디자인을 위한 포괄적인 가이드

* Library dependendcy 다운로드

![image-20200416092704919](images/image-20200416092704919.png)

* dependency 추가 확인

![image-20200416092849419](images/image-20200416092849419.png)

## 1. TabLayout

<img src="images/image-20200416095118562.png" alt="image-20200416095118562" style="zoom:67%;" />

![image-20200416095614974](images/image-20200416095614974.png)

![image-20200416095952100](images/image-20200416095952100.png)

```xml
app:tabMode="fixed"       --- tab이 고정될 때
app:tabMode="scrollable"  --- tab이 많을 때 scroll 이동
             
```
* 탭 추가

```java
tabLayout.addTab(tabLayout.newTab().setText("설정"));
```

* 처음 실행할 때 보여줄 프래그먼트 지정

```java
        getSupportFragmentManager().beginTransaction().
                replace(R.id.content_container,firstFragment).commit();
```

* 탭에 이벤트 연결하기 *- setOnTabSelectedListener는 deprecated된 메서드로 addOn~ 써주기!*

![image-20200416104440049](images/image-20200416104440049.png)

## 2. BottomNavigationView

![image-20200416095924761](images/image-20200416095924761.png)

* LinearLayout의 layout_weigth = 1을 주어야 bottomlayout이 밑으로 붙을 수 있다.

![image-20200416095532569](images/image-20200416095532569.png)

* resource 생성

![image-20200416101254651](images/image-20200416101254651.png)

![image-20200416103737924](images/image-20200416103737924.png)

![image-20200416105008001](images/image-20200416105008001.png)



![image-20200416101430971](images/image-20200416101430971.png)

![image-20200416101525998](images/image-20200416101525998.png)

* 아이콘 변경

![image-20200416103757399](images/image-20200416103757399.png)

* layout에 삽입

<img src="images/image-20200416104051662.png" alt="image-20200416104051662" style="zoom: 80%;" />

*[결과]*

*이렇게 BottomLayout에 아이콘과 text로 삽입되어 들어온다*

![image-20200416104147061](images/image-20200416104147061.png)

* `BottomNavigationView`이벤트 연결

```java
bottomNavigationView.setOnNavigationItemSelectedListener(new BottomNavigationView.OnNavigationItemSelectedListener() {
            @Override
            public boolean onNavigationItemSelected(@NonNull MenuItem menuItem) {
                if(menuItem.getItemId()==R.id.bottom_item2){
                    getSupportFragmentManager().beginTransaction().
                            replace(R.id.content_container,secondFragment).commit();
                }
                return false;
            }
        });
```

## 3. OptionMenu

* 액티비티가 만들어질 때 자동으로 호출되는 메소드 - 이 메소드 안에서 메뉴를 생성
  * true 만 리턴하면 메뉴를 만든다

![image-20200416112353572](images/image-20200416112353572.png)

* 옵션 메뉴의 아이템을 선택하면 자동으로 호출되는 메소드

![image-20200416112430266](images/image-20200416112430266.png)

## 4. Action Bar

* **ListView**
  * adapter: 항목에 대한 리스트를 리스트 뷰 데이터의 형식에 맞게 뿌려주는 역할

![image-20200416130606593](images/image-20200416130606593.png)

* **showAsAction**

![image-20200416113137472](images/image-20200416113137472.png)

* `always` : 메뉴를 항상 액션바에 표시하겠다
* `collapseActionView` : 접었다 폈다 할 수 있는 메뉴
* `withText` : 텍스트와 아이콘을 같이 보여줄 수 있는 기능

*[always + withText]*

![image-20200416114035187](images/image-20200416114035187.png)

<img src="images/image-20200416131059219.png" alt="image-20200416131059219" style="zoom:67%;" />

<img src="images/image-20200416130420285.png" alt="image-20200416130420285" style="zoom:80%;" />

* `app:actionViewClass="androidx.appcompat.widget.SearchView` : 선택되면 해당 클래스를 열겠다는 의미
  * <img src="images/image-20200416130505626.png" alt="image-20200416130505626" style="zoom:67%;" />

![image-20200416115014179](images/image-20200416115014179.png)

<img src="images/image-20200416130312144.png" alt="image-20200416130312144" style="zoom:67%;" />

## 5. AppBar 

> ActionBar + ToolBar



![image-20200416132523438](images/image-20200416132523438.png)

![image-20200416132629580](images/image-20200416132629580.png)



<img src="images/image-20200416132709277.png" alt="image-20200416132709277" style="zoom:67%;" />



## 6. Toolbar

* 10 버전 라이브러리인지 확인 잘 하기

* Toolbar는 find해서 사용해야 하며 직접 만든 디자인을 연결할 수 있다.

  * 같은 기능이지만 확장 가능성이 있음

  * ```java
    import androidx.appcompat.widget.Toolbar;
    ```

  * 

* ![image-20200416134107489](images/image-20200416134107489.png)

* ActionBar 없애기
  
  * res - values - styles.xml

![image-20200416134231082](images/image-20200416134231082.png)

* Toolbar가 사라진 것을 볼 수 있음

<img src="images/image-20200416134356582.png" alt="image-20200416134356582" style="zoom:67%;" />



* 액션바 대신 툴바를 사용하겠다고 정의

  ```javascript
  setSupportActionBar(toolbar);
  ```

* ActionBar와 같은 기능이 가능함을 볼 수 있음

![image-20200416135227977](images/image-20200416135227977.png)

### 1. :jack_o_lantern: :AppBarLayout

<img src="images/image-20200416143342671.png" alt="image-20200416143342671" style="zoom: 67%;" />

<img src="images/image-20200416143927340.png" alt="image-20200416143927340" style="zoom:67%;" />

<img src="images/image-20200416144059860.png" alt="image-20200416144059860" style="zoom:67%;" />

![image-20200416145434965](images/image-20200416145434965.png)

* floatingActionButton

![image-20200416145116785](images/image-20200416145116785.png)

<img src="images/image-20200416145333589.png" alt="image-20200416145333589" style="zoom:50%;" />

![image-20200416150617318](images/image-20200416150617318.png)

* abbBar이용한 floating Action button
  * NestedScrollView 기본 설정됨

<img src="images/image-20200416150632994.png" alt="image-20200416150632994" style="zoom: 67%;" />

<img src="images/image-20200416151004987.png" alt="image-20200416151004987" style="zoom: 80%;" />

### 2. 대화 상자 만들기 :iphone:



<img src="images/image-20200416152512138.png" alt="image-20200416152512138" style="zoom:67%;" />

* FloatingActionButton을 눌렀을 때 대화상자가 뜨고 입력한 데이터가 리스트 뷰에 추가가 되도록 구현
  * xml을 객체로 만들어 펼쳐놓을 `LayoutInflater` 사용

![image-20200416154011280](images/image-20200416154011280.png)

[결과]

![image-20200416154106698](images/image-20200416154106698.png)

<img src="images/image-20200416154250181.png" alt="image-20200416154250181" style="zoom:80%;" />

![image-20200416154719898](images/image-20200416154719898.png)

<img src="images/image-20200416154747871.png" alt="image-20200416154747871" style="zoom:67%;" />

![image-20200416154817350](images/image-20200416154817350.png)

### 3. with Tabs

<img src="images/image-20200416160715682.png" alt="image-20200416160715682" style="zoom:50%;" />

![image-20200416160949230](images/image-20200416160949230.png)

* new Fragment

  * 액티비티와 통신하는 방법

  ![image-20200416161634903](images/image-20200416161634903.png)

  * inflate시켜놓은 view로 부터 findViewById

  * fragment를 만들면서  title을 setting시킬 수 있도록 작업

    ![image-20200416162017746](images/image-20200416162017746.png)

  * 탭 생성

  ![image-20200416162735136](images/image-20200416162735136.png)

  [결과]

  ![image-20200416162516412](images/image-20200416162516412.png)

  * FragmentStatePagerAdapter

    ![image-20200416165346787](images/image-20200416165346787.png)

    * TabLayout과 ViewPager를 연결

      - ViewPager의 getPageTitle메소드를 호출해서 탭의 문자열을 셋팅
      - getPageTitle 이 없다면 Tab과 연결된 문자열이 출력되지 않는다.
      - `setupWithViewPager` 메소드 내부에서 **탭의 문자열을 출력하기 위해서** 호출된다

      ```java
      tabLayout.setupWithViewPager(pager);
      ```

      

  <img src="images/image-20200416165138461.png" alt="image-20200416165138461" style="zoom:80%;" />
  
  [실습]
  
  * layout  - TabLayout 추가
  
  ![image-20200416175544713](images/image-20200416175544713.png)
  
  * TabList  추가
  
  ![image-20200416174854711](images/image-20200416174854711.png)
  
  * Tab과 문자열 연동
  
  ![image-20200416174915501](images/image-20200416174915501.png)
  
  <img src="images/image-20200416175526519.png" alt="image-20200416175526519" style="zoom:50%;" />

## HomeButton

* 안드로이드에서 제공해주는 id는` android.R.id.~` 로 작성

![image-20200416142430928](images/image-20200416142430928.png)



<img src="images/image-20200416142047234.png" alt="image-20200416142047234" style="zoom:67%;" />







