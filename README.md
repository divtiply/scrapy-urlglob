scrapy-expand-start-urls
========================

Expand start urls using curl-like url globbing sequence.
See https://curl.haxx.se/docs/manpage.html#URL for expansion rules.

Usage
-----

This module can be plugged into scrapy with spider mixin:
```python
from scrapy.spiders import Spider
from scrapy_expand_start_urls import ExpandStartUrlsSpiderMixin

class ExampleSpider(Spider, ExpandStartUrlsSpiderMixin):
    start_urls = ['https://example.com/{foo,bar}?page=[1-3]']
```

or by enabling spider middleware in the `settings.py`:
```python
SPIDER_MIDDLEWARES.update({
    'scrapy_expand_start_urls.ExpandStartUrlsSpiderMiddleware': 490,
})
```

Settings
--------

* `EXPAND_START_URLS_ENABLED`\
   default: `True`

License
-------

[MIT](https://choosealicense.com/licenses/mit/)
