scrapy-urlglob
==============

Expand start urls using curl-like url globbing sequence.  
See https://curl.haxx.se/docs/manpage.html#URL for expansion rules.
```
>>> for url in expand_url('https://example.com/{foo,bar}?page=[1-3]'):
...     print(url)
https://example.com/foo?page=1
https://example.com/foo?page=2
https://example.com/foo?page=3
https://example.com/bar?page=1
https://example.com/bar?page=2
https://example.com/bar?page=3
>>> for url in expand_url('https://example.com?page=[01-10:3]'):
...     print(url)
https://example.com?page=01
https://example.com?page=04
https://example.com?page=07
https://example.com?page=10
>>> for url in expand_url('https://[a-z:10].example.com'):
...     print(url)
https://a.example.com
https://k.example.com
https://u.example.com
```

Usage
-----

This module can be plugged into scrapy with spider mixin:
```python
from scrapy.spiders import Spider
from scrapy_urlglob import ExpandStartUrlsMixin

class ExampleSpider(Spider, ExpandStartUrlsMixin):
    start_urls = ['https://example.com/{foo,bar}?page=[1-3]']
```

or by enabling spider middleware in the `settings.py`:
```python
SPIDER_MIDDLEWARES.update({
    'scrapy_urlglob.ExpandStartUrlsMiddleware': 490,
})
```

Settings
--------

* `URLGLOB_ENABLED`\
   default: `True`

License
-------

[MIT](LICENSE.txt)
