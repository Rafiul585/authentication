<h1>User management with Django allauth</h1>


<h3># Install django-allauth</h3>
<p>pip install django-allauth</p>


<h3># Django allauth settings.py configuration</h3>
<p>
    INSTALLED_APPS = [
    'django.contrib.sites',
    'allauth',
    'allauth.account',
    'allauth.socialaccount',
]
</p>


<h3># Ensure SITE_ID is set sites app</h3>
<p>SITE_ID = 1</p>

<h3># Add the 'allauth' backend to AUTHENTICATION_BACKEND and keep default ModelBackend</h3>
<p>AUTHENTICATION_BACKENDS = [ 'django.contrib.auth.backends.ModelBackend',
    'allauth.account.auth_backends.AuthenticationBackend']</p>

<p># EMAIL_BACKEND so allauth can proceed to send confirmation emails</p>
<p># ONLY for development/testing use console</p>
<p>EMAIL_BACKEND='django.core.mail.backends.console.EmailBackend'</p>

<h3># Custom allauth settings</h3>
<h3># Use email as the primary identifier</h3>

<p>ACCOUNT_AUTHENTICATION_METHOD = 'email' 
    ACCOUNT_EMAIL_REQUIRED = True</p>

<h3># Make email verification mandatory to avoid junk email accounts</h3>
<p>ACCOUNT_EMAIL_VERIFICATION = 'mandatory' </p>

<h3># Eliminate need to provide username, as it's a very old practice</h3>
<p>ACCOUNT_USERNAME_REQUIRED = False</p>

<h3># Django allauth url configuration</h3>
<p>urlpatterns = [
    url(r'^accounts/', include('allauth.urls')),
]</p>
