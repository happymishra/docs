# Django ORM examples

Models
```python
class Author(models.Model):
    name = models.CharField(max_length=255)
    email = models.EmailField()
    age = models.IntegerField()

    def __str__(self):
        return self.name
    
    
class Article(models.Model):
    title = models.CharField(max_length=120)
    description = models.TextField()
    body = models.TextField()
    author = models.ForeignKey('Author',
                                related_name='articles',
                                on_delete=models.CASCADE)

    def __str__(self):
        return self.title

```

----------------------------------------------------------------------

### Get SQL query 

```python
a = Article.objects.all()

print(str(a.query))
```


-----------------------------------------------------------------------
### ORM examples
-----------------------------------------------------------------------

```python
a = Article.objects.all()

# SQL Query
'SELECT "article_author"."id", "article_author"."name", "article_author"."email", "article_author"."age" 
FROM "article_author"'

```

```python
# Greater than
a = Author.objects.filter(age__gt=20)
```

```python
# And condition
a = Author.objects.filter(age__gt=20, name='Rupesh')
```

```python
# OR condition

from django.db.models import Q
a = Author.objects.filter(Q(age__gt=20)| Q(name='Rupesh'))
```

```python
# AND and OR together
a = Author.objects.filter(Q(age__gt=20)| Q(name='Rupesh'), email='rupesh@gmail.com')
```

```python
# NOT query
from django.db.models import Q

a = Author.objects.filter(~Q(age__gt=20))
a = Author.objects.exclude(age__gt=20)
```

```python
# Exists true or false. More efficient then count
Author.objects.filter(age=25).exists()
```

```python
# INNER JOIN in django
a = Article.objects.select_related('author')
```

```python
# Select only required columns. This return list of dicts
a = Article.objects.select_related('author').values('author__name', 'title')
```

```python
# Return list of tuples
a = Article.objects.select_related('author').values_list('author__name', 'title')
```

```python
#ONly and defer
a = Article.objects.select_related('author').defer('title', 'description')
a = Article.objects.only('title', 'description')
```

```python
# Annotate. SELECT col as NewCOl
from django.db.models import F

a = Article.objects.select_related('author').annotate(a_name=F('author__name'), art_title=F('title')).values('a_name', 'art_title')

```

```python
# Select constant columns
a = Article.objects.select_related('author').annotate(a_name=F('author__name'), art_title=F('title')).extra(select={'indentation':'0'}).values('indentation', 'a_name')
```

```python
# Count
a = Author.objects.annotate(name_count=Count('name'))
```

```python
 a = Author.objects.all().aggregate(Avg('age'))
```

```python
a = Author.objects.all().aggregate(Avg('age'), Max('age'), Min('age'))
```