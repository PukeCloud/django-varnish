Django Varnish
================

Varnish is a state-of-the-art, high-performance HTTP accelerator.
For more information checkout `Varnish Site <http://varnish.projects.linpro.no/>`_

Django Varnish works with Varnish server(s) to manage caching of object pages.
It allows you to monitor certain models and when they are updated,
Django Varnish will purge the model's absolute_url on your frontend(s).
This ensures that object detail pages are served blazingly fast and are always up to date.
You may also go in and manually tweak things (such as your VCL configuration) using a management command. 

Django Varnish requires the `varnish python bindings <http://github.com/justquick/python-varnish>`_

Put ``varnishapp`` in your ``INSTALLED_APPS`` then set a few more settings.

``VARNISH_WATCHED_MODELS`` is a list of installed models whose absolute_urls you want to purge from your
Varnish cache upon saving. Example: ``('auth.user','profiles.profile')``

``VARNISH_MANAGMENT_ADDRS`` is a list of Varnish cache addresses (containing their management ports).
Example ``('server1:6082','server2:6082')``


The management command ``varnishmgt`` is also now available and just blindly executes passes commands and prints the results.
Example ``$ ./manage.py varnishmgt purge_url "/"``