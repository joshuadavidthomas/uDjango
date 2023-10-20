# 🧬 μDjango (micro Django)

A single file Django micro project created for demonstration purposes to be used in the same way as other Python frameworks.

## 🏛️ History

I created this code while working on an improvement to [Will Vincent](https://github.com/wsvincent)'s [Django Microframework](https://github.com/wsvincent/django-microframework) repository, which was itself inspired by a talk that [Carlton Gibson](https://github.com/carltongibson) gave at [DjangoCon US 2019](https://2019.djangocon.us/talks/using-django-as-a-micro-framework-on-the/): _"[Using Django as a Micro-Framework](https://www.youtube.com/watch?v=w9cYEovduWI)"_.

Starting from that demonstration code I thought of a `Django` micro application that could be used in the same way as a minimal application used in other `Python` frameworks such as `Flask` or `FastAPI`.

I presented this code during the [first sprint day](https://2023.djangocon.us/sprints/thursday/) of [DjangoCon US 2023](https://2023.djangocon.us), together with [Will Vincent](https://github.com/wsvincent) and seeing the appreciation I decided to publish it in this repository.

[![μDjango presentation during the DjangoCon US 2023 sprints in Durham, North Carolina](https://cdn.fosstodon.org/media_attachments/files/111/262/282/120/320/402/original/0b644dcffe2eeecf.jpg)](https://fosstodon.org/@paulox/111262287902120294)

> μDjango presentation during the DjangoCon US 2023 sprints in Durham, North Carolina

## 💻 Set Up

### ⚗️ Virtualenv

Creating and activating the virtual environment:

```console
$ python3 -m venv .venv
$ source .venv/bin/activate
```

### 🧩 Requirements

Installing the required python packages in the virtual environments:

```console
$ python3 -m pip install django uvicorn
```
## 🧮 Code

Create a new file called `udjango.py` and update it as follows:

```python
from django.conf import settings
from django.core.handlers import asgi
from django.http import JsonResponse
from django.urls import path

settings.configure(ALLOWED_HOSTS="*", ROOT_URLCONF=__name__)

app = asgi.ASGIHandler()


async def root(request):
    return JsonResponse({"message": "Hello World"})


urlpatterns = (path("", root),)
```

## 🏃 Run

Start the server with `uvicorn` command.

```console
$ uvicorn udjango:app --reload
```

## 🔬 Check it

Open your browser at [http://127.0.0.1:8000](http://127.0.0.1:8000)

You will see the JSON response as:

```json
{"message": "Hello World"}
```

## ⚠️ Disclaimer

This code is for demonstration purposes only and should not be used in production. However, the code is released without any guarantee from the author and no liability can be attributed. Use at your own risk.

## ⚖️ License

**μDjango** is licensed under the [BSD 3-Clause License](https://github.com/pauloxnet/uDjango/blob/main/LICENSE).

## 👥 Authors

### 👤 Paolo Melchiorre

-   🌍 Blog: [www.paulox.net](https://www.paulox.net)
-   🐙 Github: [@pauloxnet](https://github.com/pauloxnet)
-   🦣 Mastodon: [@paulox@fosstodon.org](https://fosstodon.org/@paulox)
-   🐦️ Twitter: [@pauloxnet](https://twitter.com/pauloxnet)
