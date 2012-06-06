xmlparse
========

XML Parser for Python.  Easily convert awful XML into awesome JSON.

Usage
-----

Use this module in your python code by including it and using the
`xmltodict()` function.

``` python
>>> import XMLParser
>>> xml = open('./example.xml', 'r').read()
>>> XMLParser.xmltodict(xml)
{u'sites': [{'attr': {}, 'child': {u'site': [{'attr': {u'rating': u'5'}, 'child': {u'url': [{'attr': {}, 'child': u'http://www.daveeddy.com'}], u'title': [{'attr': {}, 'child': u'Dave Eddy'}]}}, {'attr': {u'rating': u'4'}, 'child': {u'url': [{'attr': {}, 'child': u'http://lightsandshapes.com'}], u'title': [{'attr': {}, 'child': u'Lights and Shapes'}]}}, {'attr': {u'rating': u'3', u'nsfw': u'false'}, 'child': {u'url': [{'attr': {}, 'child': u'http://www.duckduckgo.com'}], u'title': [{'attr': {}, 'child': u'Duck Duck Go'}]}}]}}]}
>>>
```

Command Line
------------

Give an XML file as an argument to XMLParser.py, or pass in XML on stdin.

    dave @ [ bahamas10 :: (SunOS) ] ~/dev/xmlparse $ cat example.xml
    <sites>
    	<site rating="5">
    		<title>Dave Eddy</title>
    		<url>http://www.daveeddy.com</url>
    	</site>
    	<site rating="4">
    		<title>Lights and Shapes</title>
    		<url>http://lightsandshapes.com</url>
    	</site>
    	<site rating="3" nsfw="false">
    		<title>Duck Duck Go</title>
    		<url>http://www.duckduckgo.com</url>
    	</site>
    </sites>
    dave @ [ bahamas10 :: (SunOS) ] ~/dev/xmlparse $ ./XMLParser.py example.xml
    {
        "sites": [
            {
                "attr": {},
                "child": {
                    "site": [
                        {
                            "attr": {
                                "rating": "5"
                            },
                            "child": {
                                "url": [
                                    {
                                        "attr": {},
                                        "child": "http://www.daveeddy.com"
                                    }
                                ],
                                "title": [
                                    {
                                        "attr": {},
                                        "child": "Dave Eddy"
                                    }
                                ]
                            }
                        },
                        {
                            "attr": {
                                "rating": "4"
                            },
                            "child": {
                                "url": [
                                    {
                                        "attr": {},
                                        "child": "http://lightsandshapes.com"
                                    }
                                ],
                                "title": [
                                    {
                                        "attr": {},
                                        "child": "Lights and Shapes"
                                    }
                                ]
                            }
                        },
                        {
                            "attr": {
                                "rating": "3",
                                "nsfw": "false"
                            },
                            "child": {
                                "url": [
                                    {
                                        "attr": {},
                                        "child": "http://www.duckduckgo.com"
                                    }
                                ],
                                "title": [
                                    {
                                        "attr": {},
                                        "child": "Duck Duck Go"
                                    }
                                ]
                            }
                        }
                    ]
                }
            }
        ]
    }
    dave @ [ bahamas10 :: (SunOS) ] ~/dev/xmlparse $ cat example.xml | ./XMLParser.py | json -i
    { sites:
       [ { attr: {},
           child:
            { site:
               [ { attr: { rating: '5' },
                   child:
                    { url: [ { attr: {}, child: 'http://www.daveeddy.com' } ],
                      title: [ { attr: {}, child: 'Dave Eddy' } ] } },
                 { attr: { rating: '4' },
                   child:
                    { url: [ { attr: {}, child: 'http://lightsandshapes.com' } ],
                      title: [ { attr: {}, child: 'Lights and Shapes' } ] } },
                 { attr: { rating: '3', nsfw: 'false' },
                   child:
                    { url: [ { attr: {}, child: 'http://www.duckduckgo.com' } ],
                      title: [ { attr: {}, child: 'Duck Duck Go' } ] } } ] } } ] }

Copying
=======

Released under the BSD 3-clause license, see LICENSE for details.
