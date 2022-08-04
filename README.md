User management with Django allauth

Install and setup django-allauth
pip install django-allauth


Django allauth settings.py configuration

INSTALLED_APPS = [
    # Django sites app  required
    'django.contrib.sites',
    'allauth',
    'allauth.account',
    'allauth.socialaccount',
]

# Ensure SITE_ID is set sites app 
SITE_ID = 1

# Add the 'allauth' backend to AUTHENTICATION_BACKEND and keep default ModelBackend
AUTHENTICATION_BACKENDS = [ 'django.contrib.auth.backends.ModelBackend',
                           'allauth.account.auth_backends.AuthenticationBackend'] 
# EMAIL_BACKEND so allauth can proceed to send confirmation emails
# ONLY for development/testing use console 
EMAIL_BACKEND='django.core.mail.backends.console.EmailBackend'

# Custom allauth settings
# Use email as the primary identifier
ACCOUNT_AUTHENTICATION_METHOD = 'email' 
ACCOUNT_EMAIL_REQUIRED = True

# Make email verification mandatory to avoid junk email accounts
ACCOUNT_EMAIL_VERIFICATION = 'mandatory' 

# Eliminate need to provide username, as it's a very old practice
ACCOUNT_USERNAME_REQUIRED = False

Django allauth url configuration
urlpatterns = [
    url(r'^accounts/', include('allauth.urls')),
]
