# ViewPager

화면 전환을 위해서 ViewPager를 사용하는 경우 (ListView와 동일)

>1. ViewPager에 담을 데이터 - View, Fragment
>
>2. Adapter 커스터마이징
>
>3. ViewPAger에 Adapter연결하기

1. **ViewPager에 담을 데이터**

![image-20200414133619154](C:\Users\student\AppData\Roaming\Typora\typora-user-images\image-20200414133619154.png)

2. **Adapter 커스터마이징**

![image-20200414133859558](C:\Users\student\AppData\Roaming\Typora\typora-user-images\image-20200414133859558.png)

3. **ViewPager에 어댑터 연결**

```java
        MainPagerAdapter adapter = new MainPagerAdapter();
        mainPager.setAdapter(adapter);
```

<img src="images/image-20200414154850503.png" alt="image-20200414154850503" style="zoom:80%;" />

## FragmentPagerAdapter

![image-20200414163439567](images/image-20200414163439567.png)

```java
 MainPagerAdapter adapter
                = new MainPagerAdapter(getSupportFragmentManager(),viewlist.size());
        mainPager.setAdapter(adapter);
        mainPager.addOnPageChangeListener(new PageListener());
```



![image-20200414155039496](images/image-20200414155039496.png)

![image-20200414155050576](images/image-20200414155050576.png)

## ListFragment

* List를 뿌려주는 Fragment

![image-20200414162002703](images/image-20200414162002703.png)

* Manifest

![image-20200414163344435](images/image-20200414163344435.png)

* 위치 기반 서비스 맵을 사용하는 앱이 없도록 map 사용하는 앱은 삭제해주어야 한다.

<img src="images/image-20200414163130181.png" alt="image-20200414163130181" style="zoom:80%;" />

* 안드로이드 앱을 설치할 때 Library를 같이 설치하도록 한다.
* 라이브러리 확인하기 - library dependency

![image-20200414164801695](images/image-20200414164801695.png)