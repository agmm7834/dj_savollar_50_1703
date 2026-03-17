### 💻 Django savollar 50 ta

**1.** Quyidagi buyruqlar bajarildi. Natijada loyihada nima hosil bo‘ladi va qaysi fayl asosiy ishga tushiradi?

```bash
python -m venv venv
source venv/bin/activate
pip install django
django-admin startproject mysite
```

**2.** `manage.py runserver` ishlamayapti. Ehtimoliy sabablar nima bo‘lishi mumkin?

**3.** Quyidagi model mavjud:

```python
class Product(models.Model):
    name = models.CharField(max_length=50)
    price = models.DecimalField(max_digits=10, decimal_places=2)
```

Agar `makemigrations` qilinmasa va `migrate` bajarilsa, nima sodir bo‘ladi?

**4.** Quyidagi view ishlatilmoqda:

```python
def detail(request, id):
    return HttpResponse(f"ID: {id}")
```

urls.py da:

```python
path('item/<int:id>/', views.detail)
```

Brauzerga `/item/abc/` yozilsa, nima bo‘ladi?

**5.** Quyidagi kod ishlamayapti:

```python
# urls.py
urlpatterns = [
    path('home', home),
]
```

Xatoni aniqlang va to‘g‘ri yozish shaklini tushuntiring.

**6.** Quyidagi modelga yangi field qo‘shildi:

```python
class Post(models.Model):
    title = models.CharField(max_length=100)
    content = models.TextField()
    published = models.BooleanField(default=False)
```

Qaysi ketma-ket buyruqlar to‘g‘ri migratsiya qiladi?

**7.** Quyidagi template kodi ishlatilmoqda:

```html
<h1>{{ post.title }}</h1>
<p>{{ post.content }}</p>
```

Agar `post` object view’dan yuborilmasa, natija qanday bo‘ladi?

**8.** Quyidagi view kodi:

```python
def posts_list(request):
    posts = Post.objects.all()
    return render(request, 'blog/list.html', {'posts': posts})
```

Agar `Post` modelida bitta ham object bo‘lmasa, template qanday natija beradi?

**9.** Quyidagi kod ishlatilmoqda:

```python
path('blog/', include('blog.urls'))
```

`blog.urls` faylida `urlpatterns = []` bo‘lsa, `/blog/` ga kirilsa nima bo‘ladi?

**10.** Quyidagi model mavjud:

```python
class Comment(models.Model):
    post = models.ForeignKey(Post, on_delete=models.CASCADE)
    text = models.TextField()
```

Agar `Post` object o‘chirib yuborilsa, `Comment` nima bo‘ladi?

**11.** Quyidagi kodni tushuntiring:

```python
Post.objects.get(id=5)
```

Agar object topilmasa, nima sodir bo‘ladi?

**12.** Quyidagi holatda template ishlamaydi:

```python
return render(request, 'blog/index.html')
```

`index.html` `templates` papkasida bo‘lsa ham ishlamasa, ehtimoliy sabab nima?

**13.** Quyidagi kodda nima muammo bor?

```python
class Post(models.Model):
    title = models.CharField(max_length=100)

    def __str__(self):
        return self.id
```

**14.** Quyidagi view kodida xatolik:

```python
def home(request):
    return render(request, 'home.html', context)
```

Xatolik nima va uni qanday tuzatish mumkin?

**15.** Quyidagi view va urls mavjud:

```python
# views.py
def detail(request, pk):
    post = Post.objects.get(id=pk)
    return render(request, 'detail.html', {'post': post})

# urls.py
path('post/<int:pk>/', views.detail)
```

Agar `pk` mavjud bo‘lmagan id bo‘lsa, brauzerda nima ko‘rinadi?

**16.** Quyidagi template kodi ishlatilmoqda:

```html
{% for post in posts %}
    <h2>{{ post.title }}</h2>
{% empty %}
    <p>No posts available.</p>
{% endfor %}
```

`posts` queryset bo‘sh bo‘lsa, nima chiqaradi?

**17.** Quyidagi kodda nima xato?

```python
class Author(models.Model):
    name = models.CharField(max_length=50)
    
    def get_absolute_url(self):
        return reverse('author_detail', args=[self.pk])
```

`reverse` ishlashi uchun nima kerak?

**18.** Quyidagi kod ishlatilmoqda:

```python
INSTALLED_APPS = []
```

Agar loyihada `blog` app yaratilgan bo‘lsa, nima xato bo‘ladi?

**19.** Quyidagi queryset nimani qaytaradi?

```python
posts = Post.objects.filter(created_at__year=2026)
```

**20.** Agar `urls.py` da `path('', views.home)` yozilgan bo‘lsa va brauzerga `/home/` kirilsa, nima bo‘ladi?

---

**21.** Quyidagi template ishlamayapti:

```html
<h1>{{ user.username }}</h1>
```

Agar view’dan `user` yuborilmagan bo‘lsa, natija nima bo‘ladi?

**22.** Quyidagi modelda `on_delete=models.SET_NULL` ishlatilsa, Post o‘chirilsa Comment nima bo‘ladi?

```python
post = models.ForeignKey(Post, on_delete=models.SET_NULL, null=True)
```

**23.** Quyidagi queryset:

```python
Post.objects.filter(title='Django Tutorial').order_by('-created_at')
```

Natija qanday tartibda chiqadi?

**24.** Agar view quyidagicha yozilgan bo‘lsa:

```python
def my_view(request):
    posts = Post.objects.all()
    return render(request, 'list.html', {'posts': posts})
```

Template’da `{{ posts.0.title }}` ishlatilsa, nima sodir bo‘ladi?

**25.** Quyidagi modelda `unique=True` ishlatilsa, nima vazifa bajariladi?

```python
slug = models.SlugField(unique=True)
```

**26.** `makemigrations` va `migrate` buyruqlarining farqini tushuntiring.

**27.** Agar `urlpatterns` bo‘sh bo‘lsa, Django serveri `/` ga kirganda nima qiladi?

**28.** Quyidagi template kodi:

```html
{% if post.published %}
    <p>Published</p>
{% else %}
    <p>Draft</p>
{% endif %}
```

`post.published=None` bo‘lsa, nima ko‘rinadi?

**29.** Agar view-da `redirect('home')` ishlatilsa, foydalanuvchi brauzerda nima ko‘radi?

**30.** Agar `ForeignKey`da `related_name` berilsa, nimani o‘zgartiradi?

**31.** Quyidagi view ishlatilmoqda:

```python
def archive(request, year):
    posts = Post.objects.filter(created_at__year=year)
    return render(request, 'archive.html', {'posts': posts})
```

`year` int bo‘lmagan qiymat bilan yuborilsa, nima bo‘ladi?

**32.** `settings.py` da `DEBUG=False` va `ALLOWED_HOSTS=[]` bo‘lsa, server qanday ishlaydi?

**33.** Template’da `{% url 'post_detail' post.id %}` ishlatilmoqda. Agar urls.py da `name='post_detail'` berilmagan bo‘lsa, nima sodir bo‘ladi?

**34.** Agar modelda `default` qiymat berilmasa va field `blank=False`, yangi object yaratishda nima bo‘ladi?

**35.** Quyidagi queryset:

```python
Post.objects.exclude(title='Test Post')
```

Nimani chiqaradi?

**36.** Agar view-da `redirect('home')` ishlatilsa, foydalanuvchi brauzerda nima ko‘radi?

**37.** Quyidagi kod ishlatilmoqda:

```python
path('post/<slug:slug>/', views.post_detail)
```

Slug noto‘g‘ri formatda berilsa, nima bo‘ladi?

**38.** Agar `base.html` template ishlatilsa va `{% block content %}{% endblock %}` bo‘lsa, child template bo‘lmasa, nima sodir bo‘ladi?

**39.** `forms.py` da `ModelForm` ishlatilsa, `save(commit=False)` nima qiladi?

**40.** Agar `MEDIA_ROOT` noto‘g‘ri bo‘lsa, fayl yuklanmaydi. Qanday xatolar bo‘ladi?

**41.** Quyidagi queryset ishlatilmoqda:

```python
Post.objects.values('title')
```

Natija qaysi formatda chiqadi?

**42.** Agar `ForeignKey`da `on_delete=models.PROTECT` ishlatilsa, nima vazifa bajariladi?

**43.** Quyidagi modelda `ManyToManyField` ishlatilgan:

```python
tags = models.ManyToManyField(Tag)
```

Qanday vazifa bajaradi va migratsiya qanday bo‘ladi?

**44.** `urlpatterns` ichida bir xil path ikki marta yozilsa, qaysi biri ishlaydi?

**45.** `static()` yordamida statik fayllar sozlanadi. Agar `DEBUG=False`, nima sodir bo‘ladi?

**46.** Agar `csrf_token` template’da ishlatilmasa, POST request nima qiladi?

**47.** Queryset metodlari `all()`, `filter()`, `exclude()` farqlari nimada?

**48.** `get_object_or_404()` ishlatilmasa va object topilmasa, nima sodir bo‘ladi?

**49.** Agar Django serveri ishlayotgan bo‘lsa va model o‘zgartirilsa, nima qilish kerak, nimaga e’tibor berish kerak?

**50.** Agar `urls.py` da path noto‘g‘ri yozilgan bo‘lsa, server qanday xatolik beradi?

---

