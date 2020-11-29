Ajax signup:
# signup.html
```
{% extends 'base.html' %}

{% block javascript %}
  <script>
    $("#id_username").change(function () {
      var form = $(this).closest("form");
      $.ajax({
        url: form.attr("data-validate-username-url"),
        data: form.serialize(),
        dataType: 'json',
        success: function (data) {
          if (data.is_taken) {
            alert(data.error_message);
          }
        }
      });

    });
  </script>
{% endblock %}

{% block content %}
  <form method="post" data-validate-username-url="{% url 'validate_username' %}">
    {% csrf_token %}
    {{ form.as_p }}
    <button type="submit">Sign up</button>
  </form>
{% endblock %}
```
# views.py
```
from django.contrib.auth.models import User
from django.http import JsonResponse

def validate_username(request):
    username = request.GET.get('username', None)
    data = {
        'is_taken': User.objects.filter(username__iexact=username).exists()
    }
    if data['is_taken']:
        data['error_message'] = 'A user with this username already exists.'
    return JsonResponse(data)

```

# urls.py

```
from django.conf.urls import url
from core import views

urlpatterns = [
    url(r'^signup/$', views.SignUpView.as_view(), name='signup'),
    url(r'^ajax/validate_username/$', views.validate_username, name='validate_username'),
]
```
