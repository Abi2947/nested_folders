## Nested Folder Structure Project in Django

### Overview

This Django project demonstrates how to create a nested folder structure using models and how to manage parent-child relationships between folders.

### Setup

1. **Setup Django Project:**
   - Ensure Django is installed (`pip install django`).
   - Create a new Django project (`django-admin startproject nested_folders`).

2. **Create Django App:**
   - Create a new Django app within the project (`python manage.py startapp folders`).

3. **Define Models:**
   - Define models for `Folder` to represent the nested structure.

   ```python
   # folders/models.py
   from django.db import models

   class Folder(models.Model):
       name = models.CharField(max_length=255)
       parent = models.ForeignKey('self', on_delete=models.CASCADE, null=True, blank=True, related_name='children')

       def __str__(self):
           return self.name
   ```

4. **Register Models in Admin:**
   - Register the `Folder` model in Django admin to manage folders.

   ```python
   # folders/admin.py
   from django.contrib import admin
   from .models import Folder

   admin.site.register(Folder)
   ```

5. **Migrate Database:**
   - Apply migrations to create necessary database tables (`python manage.py makemigrations` and `python manage.py migrate`).

6. **Create Superuser:**
   - Create a superuser to access Django admin (`python manage.py createsuperuser`).
   - Use Username: **avinash** and password: **abinash2056**

7. **Access Django Admin:**
   - Start the development server (`python manage.py runserver`) and go to `http://127.0.0.1:8000/admin/` to log in with the superuser credentials.

### Usage

#### Adding Folders

1. **Add Root Folder:**
   - Navigate to Django admin and add a root folder (e.g., `parent_folder`).

2. **Add Subfolders:**
   - For each folder, you can add subfolders by selecting the parent folder (`parent_folder`) and adding new folders under it (`subfolder1`, `subfolder2`, etc.).

#### Retrieving Parent and Children

1. **Get Parent of a Subfolder:**
   - In Django model instances, you can access the parent of a subfolder using the `parent` attribute.

   ```python
   # Example to get parent of a subfolder
   subfolder = Folder.objects.get(name='subfolder2')
   parent_folder = subfolder.parent
   ```

2. **Access Children of a Parent Folder:**
   - Similarly, to access all children of a parent folder, you can use the `children` attribute.

   ```python
   # Example to get all children of a parent folder
   parent_folder = Folder.objects.get(name='parent_folder')
   children_folders = parent_folder.children.all()
   ```

### Conclusion

This project demonstrates how to implement a nested folder structure in Django using models and manage relationships between parent and child folders effectively.
while use the admin login 
