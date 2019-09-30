# Scrapy

## Start spider
```
scrapy startproject {spide name}
```

## Spider script sample:
```python
import scrapy
from SpiderName.items import ItemModel

class SpiderName(scrapy.Spider):
    name = "SpiderName"

    def start_requests(self):
        urls = [
            "url1",
            "url2"
        ]
        for url in urls:
            yield scrapy.Request(url=url, callback=self.parse)

    def parse(self, response):
                # response.css can query html page content
                # response.url can get request url
                data = response.css({pattern})
                item = ItemModel(data)
                yield item
```
## Pipeline Sample
```python
import mysql.connector
import configparser

class OpentrendPipeline(object):
    def process_item(self, item, spider):
        print(item)
        return item


class MysqlPipeline(object):

    def __init__(self):
        pass

    def open_spider(self, spider):
        config = configparser.ConfigParser()
        config.read('config.ini')
        self.conn = mysql.connector.connect(
            host=config['DATABASE']["host"],
            port=int(config['DATABASE']["port"]),
            user=config['DATABASE']["user"],
            password=config['DATABASE']["password"])
        cur = self.conn.cursor()
        cur.execute("CREATE DATABASE IF NOT EXISTS sea")
        self.conn.commit()
        cur.execute(TABLE_CREATE_SQL)
        self.conn.commit()

    def close_spider(self, spider):
        self.conn.commit()
        self.conn.close()

    def process_item(self, item, spider):
        addRow = ("INSERT INTO sea.opentrend "
                    "(name,language,description,total_star_count,fork_count,member_count,period_stars_count,period,created_dt) "
                    "VALUES (%(name)s,%(language)s,%(description)s,%(total_star_count)s,%(fork_count)s,%(member_count)s,%(period_stars_count)s,%(period)s,%(created_dt)s)"
                    )
        cur = self.conn.cursor()
        cur.execute(addRow, dict(item))
```