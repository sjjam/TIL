# Django intro

MTV : Model Template View

참고 사이트

https://docs.djangoproject.com/ko/3.0/intro/tutorial01/

https://developer.mozilla.org/ko/docs/Learn/Server-side/Django

## Start Django

1. 장고 설치

   ```bash
   $ pip install django==2.1.15
   $ pip list
   ```

2. 프로젝트 생성

   ```bash
   $ django-admin startproject <프로젝트 명>
   ```

   ```bash
   $ python manage.py runserver
   ```

3. 프로젝트 생성시 제공하는 파일

   - `manage.py`
     - 전체 django와 관련된 모든 명령어를 manage.py를 통해 실행 합니다.
   - `__init__.py`
     - 현재 `__init__.py`파일이 존재하는 폴더를 하나의 프로젝트, 혹은 패키지로 인식하게 해주는 파일
   - `settings.py`
     - 현재 프로젝트의 전체적인 설정 및 관리를 위해 존재하는 파일
   - `urls.py`
     - 내 프로젝트에 접근할 수 있는 경로를 설정하기 위한 파일
   - `wsgi.py`
     - 배포하기 위한 설정을 하는 파일

4. app 생성

   ```bash
   $ python manage.py startapp <앱 이름>
   ```

   앱 등록

   ![image-20200609170303618](images/image-20200609170303618.png)

   

----

# Django Project

------

## 프로젝트 생성

- **Project Name** : mysite
- **App Name** : articles

------

## 페이지 생성

1. **index page**
   - `/index/` : 전체 게시글 목록을 보여줄 페이지
2. **create pages **
   - `/new/` : 글 작성을 위한 form (제목, 내용) 입력 페이지
   - `/create/` : 글 작성 결과 (제목, 내용)를 출력하는 페이지

------

## 추가

1. **base template **
   - 모든 템플릿들이 상속 받을 base.html

------

## 주의사항

1. **urls.py** 설정 분리
   - app_name도 함께 설정
2. **template 폴더 구조**

-------

# Django ORM(DB 연동)

---

## CREATE

**1. INSERT INTO TABLE (column1, column2...) VALUES (values1, values2...)**

```python
# 첫번째 방법
article = Article()
article.title = 'first'
article.content = 'django!'
article.save()

# 두 번째 방법
# 어느 변수에 어떤 값을 넣을건지 명시
# id가 생략되어 있을 뿐, 자동으로 생성된다.
article = Article(title='second', content='django!')
article.save()

# 세 번째 방법
Article.objects.create(title='third', content='django!')
```

---

## READ

**2. SELECT * FROM articles_article**

```python
# 전체 조회
article = Article.objects.all()
```

**3. SELECT * FROM articles_article WHERE title='first'**

```python
# 특정 제목 불러오기
Article.objects.filter(title='first')
```

**SELECT * FROM articles_article WHERE title='first' LIMIT 1**

```python
Article.objects.filter(title='first').first()
Article.objects.filter(title='first').last()
Article.objects.filter(title='first')[0]
```

**SELECT * FROM articles_article WHERE id=1**

```python
Article.objects.get(id=1)
Article.objects.get(pk=1)
# 주의점
# 고유값이 아닌 내용을 필터링 해서
# 2개 이상의 값이 찾아지면 오류를 발생한다.
# 없는 것을 가지고 오려고 해도 오류 발생
```

**Like / startswith / endswith**

```python
# 특정 문자열을 포함 하고 있는가
Article.objects.filter(title__contains='fir')
# 특정 문자열로 시작 하는가
Article.objects.filter(title__startswith='SE')
# 특정 문자열로 끝나는가
Article.objects.filter(content__endswith='ha')
```

---

## UPDATE

**UPDATE articles_article SET title='byebye' WHERE id=1**

```python
# 수정
article = Article.objects.get(pk=1)
article.title = 'byebye'
article.save()
```

---

## DELETE

**DELETE FROM articles_article WHERE id=1**

```python
# 삭제
article = Article.objects.get(pk=1)
article.delete()
```

models.py 작성

```bash
from django.db import models

# Create your models here.
class Article(models.Model): 
    # articles_article
    title = models.CharField(max_length=150)
    content = models.TextField()
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
```



bash 명령어

```bash
$ python manage.py makemigrations
```

![image-20200615143549965](images/image-20200615143549965.png)



생성 파일 확인

![image-20200615143628723](images/image-20200615143628723.png)



```bash
$ python manage.py migrate articles
```

버전 관리

![image-20200615143657739](images/image-20200615143657739.png)



파이선 shell 창 이동

```bash
$ python manage.py shell
Python 3.7.6 (tags/v3.7.6:43364a7ae0, Dec 19 2019, 00:42:30) [MSC v.1916 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
(InteractiveConsole)
>>> from articles.models import Article 
>>> Article.objects.all()
<QuerySet []>
```



```bash
<QuerySet []>
>>> article = Article()
>>> article.title = 'first'
>>> article.content = 'django!'
>>> article
<Article: Article object (None)>
>>> article.save()
>>> article
<Article: Article object (1)>
```



조회하기

```bash
>>> article = Article.objects.all()
>>> article
<QuerySet [<Article: Article object (1)>, <Article: Article object (2)>, <Article: Article object (3)>]>
>>> article[0].title
'first'
```



조회 내용

models.py

```bash
from django.db import models

# Create your models here.
class Article(models.Model): 
    # articles_article
    title = models.CharField(max_length=150)
    content = models.TextField()
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)

    def __str__(self):
        return f'{self.id}번째글 - {self.title} : {self.content}'
```



```bash
$ python manage.py shell
Python 3.7.6 (tags/v3.7.6:43364a7ae0, Dec 19 2019, 00:42:30) [MSC v.1916 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
(InteractiveConsole)
>>> from articles.models import Article
>>> Article.objects.all()
<QuerySet [<Article: 1번째글 - first : django!>, <Article: 2번째글 - second : django!>, <Article: 3번째글 - third : django!>]>
>>> 
```



admin에 모델 등록

![image-20200615162539662](images/image-20200615162539662.png)



super 계정 생성

```bash
$ python manage.py createsuperuser
사용자 이름 (leave blank to use 'student'): admin
이메일 주소: 
Password: 
Password (again):
비밀번호가 너무 일상적인 단어입니다.
Bypass password validation and create user anyway? [y/N]: y
Superuser created successfully.
```



admin 접속 가능





# django relation 1:N

---

## CREATE

```python
# 1. 댓글 생성
comment = Comment()
comment.content = '첫번째 댓글'
comment.save()

# 2. 게시글 하나 불러오기
article = Article.objects.get(pk=1)

# 2-1. comment와 article 연결하기
comment.article = article
comment.save()

# 또 다른 방법
# 작성하는 숫자는 article의 pk값
comment.article_id = 1 # article.pk
comment.save()
```

## READ

```python
# comment 변수들 불러오기
# 1. 댓글 pk 조회
comment.pk

# 2. 댓글 content 조회
comment.content

# 3. 댓글이 어느 게시글에 연결되어 있는가
comment.article_id

# 4. 댓글이 연결된 게시글
comment.article

# 4-1. 댓글이 연결된 게시글의 제목과 내용
comment.article.pk
comment.article.title
comment.article.content

# article의 경우는?
article.comment_set.all()
```

