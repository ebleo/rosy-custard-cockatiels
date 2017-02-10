## A Small (?) Set of Notes on Various Topics  
#### Including  
- computer science
- python
- data science

***
##### Some notes about hashing:
[**Hashing**](https://en.wikipedia.org/wiki/Hash_function): a method of converting a key (string, number, piece of data,...) to a code of sorts.

![Example hash function](https://upload.wikimedia.org/wikipedia/commons/thumb/5/58/Hash_table_4_1_1_0_0_1_0_LL.svg/240px-Hash_table_4_1_1_0_0_1_0_LL.svg.png)  
In the above function, there is a collision (red hash, "02") for "John Smith" and "Sandra Dee." There are only 15 possible hashes for this algorithm.

There are a finite number of hashes possible for a particular algorithm. The strength of an algorithm can be determined by:
- how easy/difficult it is to unhash/revert the string
- how many possible hashes there are (risk of collisions)
  - collision: when two string/files share the same hash

Example algorithm: the [md5](https://en.wikipedia.org/wiki/MD5)  
Since the MD5 always returns a hash with a fixed byte amount, it is one way; the full information of the hashed object is not retained.  
- [r/eli5](https://www.reddit.com/r/explainlikeimfive/comments/21szbj/eli5_how_can_a_hash_of_a_file_ie_an_md5_checksum/) -- an explanation from reddit
- another good explaination [here](https://code.tutsplus.com/tutorials/understanding-hash-functions-and-keeping-passwords-safe--net-17577) (the explanation is from a PHP pov)  

In order to create hashes that are harder to crack, you can add [salt][1]  
***
## Python Topics/Functions
**zip()**: takes two iterables (iterables meaning something that can be iterated over, like a list), goes through both taking and combining the *i*-th element of each and forms a tuple of *i*-th iterable. Repeats until end of shortest iterable is reached.  
*example* (from [here][2]):
```python
>>> x = [1, 2, 3]
>>> y = [4, 5, 6]
>>> zipped = zip(x, y)
>>> list(zipped)
[(1, 4), (2, 5), (3, 6)]
```  
The *i*-th element of each list `x , y` is present since both lists are the same length.

Note: kind of like dot product but not really--similar in the combining the *i*-th element, but not much else.


***

<Reference>
[1]: https://en.wikipedia.org/wiki/Salt_(cryptography)
[2]: https://docs.python.org/3/library/functions.html#zip

<Comments below>
[//]: # (FOR WHATEVER REASON)
[//]: # (I can't hover over the sections to get section links, boohoo)
