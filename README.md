# NYC Geoclient Python Bindings

Python bindings for the REST [NYC Geoclient API][api].

  [api]: http://developer.cityofnewyork.us/api/geoclient-api-beta

### Usage

First, you will need to register an application with the [NYC Developer
Portal][portal], and make sure that you check off access to the Geoclient API
for the application.  Take note of the Application's ID and key.  You will not
be able to use the ID and key until [DoITT][] approves you -- this could take
several days, and you will receive an email when this happens.  There isn't any
indication of your status on the dashboard, but all requests will return a 403.

  [portal]: https://developer.cityofnewyork.us/
  [DoITT]: http://www.nyc.gov/html/doitt/html/home/home.shtml

You can `pip install` nyc-geoclient.  It depends upon the [requests][] library.

  [requests]: http://docs.python-requests.org/en/latest/index.html

    $ pip install nyc_geoclient

Once your app has been approved by DoITT, using the API is simple:

    >>> from nyc_geoclient import Geoclient
    >>> g = Geoclient('my app ID', 'my app key')

All of the REST endpoints are supported.

    >>> g.address('1500', 'Madison Ave', 'Manhattan')
    {u'assemblyDistrict': u'68',
     u'boardOfElectionsPreferredLgc': u'1',
     u'boePreferredStreetName': u'MADISON AVENUE',
     u'boePreferredstreetCode': u'12539001',
     u'boroughCode1In': u'1',
     u'censusBlock2000': u'2000',
     u'censusBlock2010': u'3003',
     u'censusTract1990': u' 168  ',
     u'censusTract2000': u' 168  ',
     u'censusTract2010': u' 168  ',
     u'cityCouncilDistrict': u'08',
     u'civilCourtDistrict': u'06',
     u'coincidentSegmentCount': u'1',
    ...

    >>> g.intersection('atlantic ave', 'nevins st', 'Brooklyn')
    {u'assemblyDistrict': u'52',
     u'boroughCode1In': u'3',
     u'censusTract1990': u'  39  ',
     u'censusTract2000': u'  39  ',
     u'censusTract2010': u'  39  ',
     u'cityCouncilDistrict': u'33',
     u'civilCourtDistrict': u'01',
     u'communityDistrict': u'302',
     u'communityDistrictBoroughCode': u'3',
     u'communityDistrictNumber': u'02',
     u'communitySchoolDistrict': u'15',
     u'congressionalDistrict': u'08',
     u'crossStreetNamesFlagIn': u'E',
     u'dcpPreferredLgcForStreet1': u'01',
     u'dcpPreferredLgcForStreet2': u'01',
     u'dotStreetLightContractorArea': u'3',
    ...

##### Errors

In cases where the geocoder does not work, it will still return a dict.  You
must look at the value for `message` to see what happened.

     >>> g.intersection('atlantic ave', 'nevins st', 'manhattan')
     {u'boroughCode1In': u'1',
     u'censusTract1990': u'      ',
     u'censusTract2000': u'      ',
     u'censusTract2010': u'      ',
     u'crossStreetNamesFlagIn': u'E',
     u'firstBoroughName': u'MANHATTAN',
     u'firstStreetNameNormalized': u'ATLANTIC AVENUE',
     u'geosupportFunctionCode': u'2',
     u'geosupportReturnCode': u'11',
     u'message': u"'ATLANTIC AVE' NOT RECOGNIZED. THERE ARE NO SIMILAR NAMES",
     u'secondStreetNameNormalized': u'NEVINS ST',
     u'streetName1In': u'ATLANTIC AVE',
     u'streetName2In': u'NEVINS ST',
     u'workAreaFormatIndicatorIn': u'C'}

The messages are generally very helpful.

### Documentation

Take a look at the [Python documentation][] for details on using the bindings,
which closely follows the [DoITT documentation][] (requires account/login).

  [Python documentation]: https://nyc-geoclient.readthedocs.org/
  [DoITT documentation]: http://developer.cityofnewyork.us/api/geoclient-api-beta

### License

BSD.
