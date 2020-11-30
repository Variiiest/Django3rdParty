# Installation
```
pip install django-contact-form
```
# Spam filtering 
```
pip install django-contact-form[akismet]
```


# urls.py
```
from django.urls import include, path


urlpatterns = [
    # ... other URL patterns for your site ...
    path('contact/', include('contact_form.urls')),
]

```

# views.py
```
from django.urls import include, path
from django.views.generic import TemplateView

from contact_form.views import ContactFormView

from yourapp.forms import YourCustomFormClass


urlpatterns = [
    # ... other URL patterns for your site ...
    path('contact/',
        ContactFormView.as_view(
            form_class=YourCustomFormClass
        ),
        name='contact_form'),
    path('contact/sent/',
        TemplateView.as_view(
            template_name='contact_form/contact_form_sent.html'
        ),
        name='contact_form_sent'),
]
```
