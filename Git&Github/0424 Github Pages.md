## Github Pages

## 정적 사이트 생성기 (generator)

.md ===> HTML/CSS , JS



jekyll(ruby)

- 오래되고 자료가 많다.

gatsby (js, react + graphql)

* 최신, 근데 유명해서 자료도 많음

### Visual studio code



* [start bootstrap](https://startbootstrap.com/)

* [visual studio code](https://code.visualstudio.com/docs/?dv=win) 

<img src="../images/image-20200423152545737.png" alt="image-20200423152545737" style="zoom: 80%;" />

* image 수정

![image-20200423153300161](../images/image-20200423153300161.png)

# Branch 병합 방법





```bash
$ git branch feature/menu

$ git branch
  feature/menu
* master

```

* 브랜치 이동 명령어 


HEAD : LinkedList 

* 이력이 다르게 관리될 뿐 파일이 사라진 것은 아니다.



```bash
$ git merge feature/menu

Updating 594c769..bb8da51
Fast-forward
 menu.txt | 0
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 menu.txt
```

```bash
$ git branch -d feature/menu
Deleted branch feature/menu (was bb8da51).
```

