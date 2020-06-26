# Pagination

## Paginator

<img src="C:\Users\sec\AppData\Roaming\Typora\typora-user-images\image-20200626103036137.png" alt="image-20200626103036137" style="zoom:80%;" />

```python
# views.py
from django.core.paginator import Paginator
```

* 한 페이지 당 3개씩, articles에 담긴 데이터 보여줄 것이다.

<img src="C:\Users\sec\AppData\Roaming\Typora\typora-user-images\image-20200626103059113.png" alt="image-20200626103059113" style="zoom:80%;" />

* index.py

  * **num** : 페이지 번호

  ```python
    {% for num in articles.paginator.page_range %}
    <a href="{% url 'articles:index' %}?page={{ num }}">{{ num }}</a>
    {% endfor %}
  ```

  ![image-20200626103756346](images/image-20200626103756346.png)