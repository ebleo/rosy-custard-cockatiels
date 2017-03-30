# Project notes
***
### Concept
Use a machine learning algorithm to provide recommendations
- [read this thingie, scholarly][2]

### Thoughts on Datatype
- Categorical
  - Tags
    - Dry
    - Crisp
    - Sweet
  - Types
    - Hard Cider
    - Beer
- Numerical
  - Ratings
    - Taste
    - Smell
- Other
  - Viscosity
  - Best mixed or pure
  - Flavor strength
    - Could be tags like:
      - Watery
      - Diluted
      - Strong
    - Or could be a sliding scale (finite resolution, or binned)

### Possible Methods
- [Collaborative Filtering][1]
  - Works by looking for similar tastes, under the assumption if 'A' feels 'X' about 'Y' issue, and 'B' feels 'X' about 'Y' issue, then for a second issue, 'Z', 'B' is more likely to feel how 'X' feels on 'Z' than a random person *because* 'A' and 'B' have common views  
  ![how CF works](https://upload.wikimedia.org/wikipedia/commons/thumb/5/52/Collaborative_filtering.gif/300px-Collaborative_filtering.gif)
- Information Filtering
  - Essentially filtering out what isn't relevant

#### Either way, need a method to extract data
- python modules
  - some quick notes here [bs4 + urllib2 vs. scrapy][5]
  - bs4 + urllib2 (put together, they're essentially a framework)
    - bs4 is a library, will do for a specified URL unless put into a loop
  - scrapy (like framework on its own)
    - apparently, meant to be simpler code for scraping
    - it's a framework and it *crawls* pages as well as processing page data
    - an [intro project][8]
      - with database info for PostGres
    - and [another][9]
      - for HTML scraping

- an API?
  - details [here][6]
  - and [there][7]
  - [tutorial][10]
##### Will this data be stored?
- Why?
- How?
  - MySQL Database
    - would need [connector][connect] for python
      - [MySQLdb][ps1]
        - one of the most popular
      - [mysql.connector][ps2]
        - [Instructions](https://dev.mysql.com/doc/connector-python/en/)
      - [PyMySQL][ps3]
        - "This package contains the pymysql module, which is written entirely in Python. It is designed to be a drop-in replacement for the MySQL-python package." [Source](https://www.a2hosting.com/kb/developer-corner/mysql/connecting-to-mysql-using-python)



### Possible sources of Data
- [Tastings][3]
  - Appears to be for alcoholic beverages in general
  - Has multiple tags for the rated alcoholic drink
    - Has groupings of tags as well as an overall (?) rating
  - *extraction notes*
    - Looking at the source code, all the information needed from each profile of item is there
- [BeerAdvocate][4]
  - Appears to have only beers?
  - User reviews as well as critics reviews (?)
    - User reviews have various numerical ratings


[1]: https://en.wikipedia.org/wiki/Collaborative_filtering
[2]: http://www.sciencedirect.com/science/article/pii/S1110866515000341
[3]: https://support.office.com/en-us/article/TYPE-function-45b4e688-4bc3-48b3-a105-ffa892995899
[4]: https://www.beeradvocate.com/
[5]: http://stackoverflow.com/questions/18837759/data-harvesting-urllib2bs4-vs-scrapy
[6]: http://www.gregreda.com/2015/02/15/web-scraping-finding-the-api/
[7]: https://schoolofdata.org/2013/11/18/web-apis-for-non-programmers/
[8]: http://newcoder.io/Intro-Scrape/
[9]: http://docs.python-guide.org/en/latest/scenarios/scrape/
[10]: https://www.codecademy.com/pt/courses/python-intermediate-en-6zbLp/0/1?curriculum_id=50ecb8cb058fd2ebda00003b

[ps1]: http://mysql-python.sourceforge.net/MySQLdb.html
[ps2]: https://www.mysql.com/products/connector/
[ps3]: https://github.com/PyMySQL/PyMySQL "Can be installed various ways"

[connect]: https://www.a2hosting.com/kb/developer-corner/mysql/connecting-to-mysql-using-python "Quick look at 3 options"
