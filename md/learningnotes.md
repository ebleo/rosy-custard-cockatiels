## A Small (?) Set of Notes on Various Topics  
#### Including  
- computer science
- python
- SQL/mySQL
- data science
- various thing I might forget
***
## Computer Science
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
[**`zip()`**][3]: takes two iterables (iterables meaning something that can be iterated over, like a list), goes through both taking and combining the *i*-th element of each and forms a tuple of *i*-th iterable. Repeats until end of shortest iterable is reached.  
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

[`repr()`][4]: There are [multiple methods of printing][5] to the console; while `print()` and `write()` give more human readable outputs, `repr()` gives output that can be read by an interpreter--it looks more like the output you would get after running a function in the command line  
*Note*: if you want multiple interpreter-like outputs, you'll have to print each one (so far as I know)
Example use of `repr()` [here][5]

### [Accessing a SQLite Database][6]
***
## SQL/mySQL
### [mySQL][sql1]
- Formatting
  - Files must be input with UTF-8 incoding (when loading in data)
    - Be sure to omit headers in data file(s)
  - Be sure to remove special characters in data, or reformat them

- Logging
  - [syslog][sql2] (have yet to figure out this one)
  - [General information][sql3]
  - How I've been going about it
    - have only had success with absolute paths
    - have not tried relative paths
  ``` sql
  tee DRIVE:/MYFOLDER/MYPATH/myloggingfile.txt
  ```
  No quotation marks are needed when giving the path.
- Linking
  - Useful to reduce redunancy (think hierarchal data)
  - [info][sql4]
***
## Data Science
### [Simplest Explanation of SVM's. Ever.][7]
From r/MachineLearning (alternatively, there's [*this*][8]...)
We have 2 colors of balls on the table that we want to separate.

![Balls on a table](http://i.imgur.com/zDBbD.png)

We get a stick and put it on the table, this works pretty well right?

![Now a stick!](http://i.imgur.com/aLZlG.png)

Some villain comes and places more balls on the table, it kind of works but one of the balls is on the wrong side and there is probably a better place to put the stick now.

![baddie, oh no!](http://i.imgur.com/kxWgh.png)

SVMs try to put the stick in the best possible place by having as big a gap on either side of the stick as possible.

![gap trick](http://i.imgur.com/ePy4V.png)

Now when the villain returns the stick is still in a pretty good spot.

![villian returns](http://i.imgur.com/BWYYZ.png)

There is another trick in the SVM toolbox that is even more important. Say the villain has seen how good you are with a stick so he gives you a new challenge.

![a new challenge :O](http://i.imgur.com/R9967.png)

There’s no stick in the world that will let you split those balls well, so what do you do? You flip the table of course! Throwing the balls into the air. Then, with your pro ninja skills, you grab a sheet of paper and slip it between the balls.

![table flipping time](http://i.imgur.com/WuxyO.png)

Now, looking at the balls from where the villain is standing, they balls will look split by some curvy line.

![and a curvy line...](http://i.imgur.com/gWdPX.png)

Boring adults the call 'balls' data, the 'stick' a classifier, the 'biggest gap trick' optimization, call 'flipping the table' kernelling and the piece of paper a hyperplane.

### [A cool classifier comparison][14]
![Comparison Table][classtable]
Classification accuracy shown in bottom right of each plot.

### Random Forests
- [Read this][19]
- Basically:
  1. Divvy up data
  1. Grow a tree for each part/chunk of data
  1. Each tree gets a vote on feature importance (1 tree, 1 vote--or something similar)
- *alternatively*, read [this][20]
  - uses a friend/movie recommendation analogy


### Quick notes

#### [Multiclass Classifiers][13]
Simply put: when classifying into on of more than 2 classes. Classification into one of 2 classes would be *binary* classification.

#### [Instance Based Learning][15]
Instance based learning relies on comparing new problems with instances seen in training, rather than focusing explicitly on generalisation.

#### Notes on the titanic excercise/decision trees:  
Decision trees don't replicate the portions of categories that each entry falls into (like a certain amount o men vs. women surviving), they simply *make decisions* based on those factors as a sort of split point.
- *Example*: The titanic decision tree says 67% to 23% female to male split--that doesn't mean that of the predicted females/males of a test data set would get that same survival ratio, it's just reflecting what the training indicates. It's a *tool for visualisation*, **not** the prediction itself. You just keep going along the splits based on where you fall, and the percentages show previously indicated likelihoods.

#### [Multiple testing][16]
Looking for testing multiple effects at once
***
### Some things not to forget
- [latent variable][9]: variables that are inferred through direct observations(example: quality of life being inferred from health, employment, social belonging...)
- [the difference of pearson correlation vs regression analysis][10]
- [Why 'X' is uppercase and 'y' is lowercase][11]
  - Linear algebra. Uppcase denotes mtx, lowercase denotes vector.
- [Why there aren't spaces when assigning fxn parameters but there are during variable assignment][12]
  - Basically doing:
    - *this* `a_function(thisVal=5, n=6)`
    - **not** this `a_function(thisVal = 5, n = 6)`
- *Bias* and *variance* have a relationship not dissimilar to accuracy and precision (read [here][darts])
- [null hypothesis][17]: the statement that two variables is *not* relationship between two variables
  - [r/eli5 post][eli5-1]
- \mu_0 (*mu not*): population mean
- **x-bar**: sample mean
- [Domingos, P. (2012). A few useful things to know about machine learning. Communications of the ACM, 55(10), 78-87.Domingos, P. (2012). A few useful things to know about machine learning. Communications of the ACM, 55(10), 78-87.][18]
  - [fraction 10^18 explained](http://stats.stackexchange.com/questions/226369/what-is-an-input-space-and-why-does-the-fraction-of-the-input-space-covered-by)
    - (10^12 / 2 ^ 100) ~= 10 ^ - 18
      - assuming all dims are binary (two categories/classifications per dim)
***
### Vocab
**panacea**: a cureall  
**disjunction**: lack of consistency
**intractable**: hard to deal with

<Reference>
[1]: https://en.wikipedia.org/wiki/Salt_(cryptography)
[2]: https://docs.python.org/3/library/functions.html#zip
[3]: https://docs.python.org/3/library/functions.html#zip
[4]: https://docs.python.org/3/library/functions.html#repr
[5]: https://docs.python.org/3/tutorial/inputoutput.html#fancier-output-formatting
[6]: http://sebastianraschka.com/Articles/2014_sqlite_in_python_tutorial.html
[7]: https://redd.it/15zrpp
[8]: http://stats.stackexchange.com/questions/2499/what-is-a-kernel-in-plain-english
[9]: https://en.wikipedia.org/wiki/Latent_variable
[10]: https://www.reddit.com/r/statistics/comments/41y4hi/pearson_correlation_vs_regression_analysis/
[11]: http://kenzotakahashi.github.io/k-nearest-neighbor-from-scratch-in-python.html
[12]: http://stackoverflow.com/questions/8853063/pep-8-why-no-spaces-around-in-keyword-argument-or-a-default-parameter-value
[13]: https://en.wikipedia.org/wiki/Multiclass_classification
[14]: http://scikit-learn.org/stable/auto_examples/classification/plot_classifier_comparison.html
[15]: https://en.wikipedia.org/wiki/Instance-based_learning
[16]: http://www.stat.berkeley.edu/~mgoldman/Section0402.pdf
[17]: https://en.wikipedia.org/wiki/Null_hypothesis
[18]: http://homes.cs.washington.edu/~pedrod/papers/cacm12.pdf
[19]: https://www.quora.com/What-is-the-difference-between-random-forest-and-decision-tress
[20]: http://blog.echen.me/2011/03/14/laymans-introduction-to-random-forests/

[sql1]: https://dev.mysql.com/doc/refman/5.7/en/ "Version 5.7"
[sql2]: https://dev.mysql.com/doc/refman/5.7/en/mysql-command-options.html#option_mysql_syslog
[sql3]: https://dev.mysql.com/doc/refman/5.7/en/mysql-logging.html
[sql4]: http://www.brighthub.com/internet/web-development/articles/70816.aspx


[eli5-1]: https://www.reddit.com/r/explainlikeimfive/comments/31gmfr/eli5_what_is_the_danger_of_underpowered_stat_sig/

[classtable]: http://scikit-learn.org/stable/_images/sphx_glr_plot_classifier_comparison_001.png "from scikit-learn page"
[darts]: http://homes.cs.washington.edu/~pedrod/papers/cacm12.pdf


<Comments below>
[//]: # (FOR WHATEVER REASON)
[//]: # (I can't hover over the sections to get section links, boohoo)


***
