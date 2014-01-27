# NYC Geoclient Python Bindings

Bindings for the REST [NYC Geoclient API][api] in Python.

  [api]: http://developer.cityofnewyork.us/api/geoclient-api-beta

### How to use

First, you will need to register an application with the [NYC Developer
Portal][portal], and make sure that you check off access to the Geoclient API
for the application.  Take note of the Application's ID and key.  You will not
be able to use the ID and key until DoITT approves you -- this could take
several days, and you will receive an email when this happens.  There isn't any
indication of your status on the dashboard, but all requests will return a 403.

  [portal]: https://developer.cityofnewyork.us/


