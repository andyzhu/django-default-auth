The accompany code is from this tutorial

https://learndjango.com/tutorials/django-login-and-logout-tutorial
https://learndjango.com/tutorials/django-signup-tutorial
https://learndjango.com/tutorials/django-password-reset-tutorial


# config/urls.py
from django.contrib import admin
from django.urls import path, include # new

urlpatterns = [
    path('admin/', admin.site.urls),
    *path('accounts/', include('django.contrib.auth.urls')), # new*
]


The **auth** app we've now included provides us with several authentication views and URLs for handling login, logout, and password management.

The URLs provided by auth are:

    accounts/login/ [name='login']
    accounts/logout/ [name='logout']
    accounts/password_change/ [name='password_change']
    accounts/password_change/done/ [name='password_change_done']
    accounts/password_reset/ [name='password_reset']
    accounts/password_reset/done/ [name='password_reset_done']
    accounts/reset/<uidb64>/<token>/ [name='password_reset_confirm']
    accounts/reset/done/ [name='password_reset_complete']

SMTP Server
In the real-world you would integrate with an email service like MailGun or SendGrid. For development purposes Django lets us store emails either in the console or as a file. We'll choose the latter and store all sent emails in a folder called sent_emails in our project directory.

To configure this, update our config/settings.py file by adding the following two lines at the bottom under our redirect URLs.

# config/settings.py
EMAIL_BACKEND = "django.core.mail.backends.filebased.EmailBackend"
EMAIL_FILE_PATH = str(BASE_DIR.joinpath('sent_emails'))

