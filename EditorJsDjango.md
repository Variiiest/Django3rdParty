# Django Editorjs

We have to install django-editorjs in our virtualenv by this command

```
pip install django-editorjs
```

After this add  in settings.py
```
INSTALLED_APPS = [
    '''',
    'django_editorjs',
    
    ''''',

]
```

In models.py add :

```
from django_editorjs import EditorJsField
 
#Add in class
  body = EditorJsField()
```
