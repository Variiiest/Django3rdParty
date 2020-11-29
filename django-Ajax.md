Ajax signup:
# signup.html
```
{% extends 'base.html' %}

{% block javascript %}
  <script>
    $("#id_username").change(function () {
      console.log( $(this).val() );
    });
  </script>
{% endblock %}

{% block content %}
  <form method="post">
    {% csrf_token %}
    {{ form.as_p }}
    <button type="submit">Sign up</button>
  </form>
{% endblock %}
```

```


```
