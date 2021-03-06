# 1 数据集简介
MovieLens数据集是一个关于电影评分的数据集，里面包含了从IMDB, The Movie DataBase上面得到的用户对电影的评分信息，详细请看下面的介绍。

## 1 links.csv
![](https://upload-images.jianshu.io/upload_images/16782311-b6eaeb6321d6ac88.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


文件里面的内容是帮助你如何通过网站id在对应网站上找到对应的电影链接的。

### 1.1 数据格式 
movieId, imdbId, tmdbId

#### 1.1.1 movieId
表示这部电影在movielens上的id，可以通过链接https://movielens.org/movies/(movieId)来得到。 
- [https://movielens.org/home](https://movielens.org/home)

![](https://upload-images.jianshu.io/upload_images/16782311-293eab773ae02784.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- [https://movielens.org/movies/1](https://movielens.org/movies/1)
![](https://upload-images.jianshu.io/upload_images/16782311-ec633757e54a0f91.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 1.1.2 imdbId
表示这部电影在imdb上的id，可以通过链接http://www.imdb.com/title/(imdbId)/ 
来得到。 
- tmdbId:表示这部电影在themoviedb上的id，可以通过链接http://www.imdb.com/title/(tmdbId)/ 
来得到。

## 2 movies.csv
movieId, title, genres 

文件里包含了一部电影的id和标题，以及该电影的类别
## 2.1 数据格式 
movieId, title, genres 

### 2.1.1 movieId
每部电影的id 

### 2.1.2 title
电影的标题 

### 2.1.3 genres
电影的类别（详细分类见readme.txt）
# 3 ratings.csv
![](https://upload-images.jianshu.io/upload_images/16782311-5556fbe423319cc1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

文件里面的内容包含了每一个用户对于每一部电影的评分。

## 3.1 数据格式 
![](https://upload-images.jianshu.io/upload_images/16782311-9bf96993f26b0edb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- userId: 每个用户的id 
- movieId: 每部电影的id 
- rating: 用户评分，是5星制，按半颗星的规模递增(0.5 stars - 5 stars) 
- timestamp: 自1970年1月1日零点后到用户提交评价的时间的秒数 

数据排序的顺序按照userId，movieId排列的。

# 4 tags.csv
![](https://upload-images.jianshu.io/upload_images/16782311-74a94880ac5e7bdb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

文件里面的内容包含了每一个用户对于每一个电影的分类

## 4.1 数据格式 
![](https://upload-images.jianshu.io/upload_images/16782311-cb36153364efb6a5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- userId: 每个用户的id 
- movieId: 每部电影的id 
- tag: 用户对电影的标签化评价 
- timestamp: 自1970年1月1日零点后到用户提交评价的时间的秒数 

数据排序的顺序按照userId，movieId排列的。

# 摘要

该数据集（ml-latest-small）描述了电影推荐服务[MovieLens]（http://movielens.org）的5星评级和自由文本标记活动。它包含9742部电影的100836个评级和3683个标签应用程序。这些数据由610位用户在1996年3月29日到2018年9月24日之间创建。该数据集于2018年9月26日生成。

随机选择用户以包含在内。所有选定的用户评分至少20部电影。不包括人口统计信息。每个用户都由一个id表示，并且不提供其他信息。

数据包含在`links.csv`，`movies.csv`，`ratings.csv`和`tags.csv`文件中。有关所有这些文件的内容和用法的更多详细信息如下。

这是一个发展的数据集。因此，它可能会随着时间的推移而发生变化，并不是共享研究结果的适当数据集。


# 引文

要确认在出版物中使用数据集，请引用以下文件：

> F. Maxwell Harper和Joseph A. Konstan。 2015.MovieLens数据集：历史和背景。 ACM交互式智能系统交易（TiiS）5,4：19：1-19：19。 <https://doi.org/10.1145/2827872>




# 文件的内容和使用


格式化和编码
-----------------------

数据集文件以[逗号分隔值]文件写入，并带有单个标题行。包含逗号（`，`）的列使用双引号（```）进行转义。这些文件编码为UTF-8。如果电影标题或标签值中的重音字符（例如Misérables，Les（1995））显示不正确，确保读取数据的任何程序（如文本编辑器，终端或脚本）都配置为UTF-8。


用户ID
--------

MovieLens用户随机选择包含。他们的ID已经匿名化了。用户ID在`ratings.csv`和`tags.csv`之间是一致的（即，相同的id指的是两个文件中的同一用户）。


电影Ids
---------

数据集中仅包含至少具有一个评级或标记的电影。这些电影ID与MovieLens网站上使用的电影ID一致（例如，id`1`对应于URL <https://movielens.org/movies/1>）。电影ID在`ratings.csv`，`tags.csv`，`movies.csv`和`links.csv`之间是一致的.

![](https://upload-images.jianshu.io/upload_images/16782311-d39a15f3551d65c8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# 2 Python 数据处理
## 2.1 转化DataFrame对象

通过[pandas.read_csv]将各表转化为pandas 的DataFrame对象
```
# 用户信息
unames = ['user_id', 'gender', 'age', 'occupation', 'zip']
users = pd.read_csv('/Volumes/doc/PyCharmProjects/MovieLenData/users.dat',
                    sep=',', header=None, names=unames, engine='python')
# 评分
rnames = ['user_id', 'movieId', 'rating', 'timestamp']
ratings = pd.read_csv('/Volumes/doc/PyCharmProjects/MovieLenData/ratings.csv',
                      sep=',', header=None, names=rnames, engine='python')
# 电影信息
mnames = ['movie_id', 'title', 'genres']
movies = pd.read_csv('/Volumes/doc/PyCharmProjects/MovieLenData/movies.csv',
                     sep=',', header=None, names=mnames, engine='python')

# 链接信息
lnames = ['movieId', 'imdbId', 'tmdbId']
links = pd.read_csv('/Volumes/doc/PyCharmProjects/MovieLenData/links.csv',
                    sep=',', header=None, names=mnames, engine='python')

# 标签信息
tnames = ['userId', 'movieId', 'tag', 'timestamp']
tags = pd.read_csv('/Volumes/doc/PyCharmProjects/MovieLenData/tags.csv',
                   sep=',', header=None, names=mnames, engine='python')
```
其中用到的参数为分隔符sep、头文件header、列名定义names、解析器引擎engine
这里和书上相比多用了engine参数，engine参数有C和Python，C引擎速度更快，而Python引擎目前功能更完整。

- 利用python的切片查看每个DataFrame
```
## 2.2  检查数据的输出
print(users[:5])
print("===================================================================")
print(ratings[:5])
print("===================================================================")
print(movies[:5])
print("===================================================================")
print(links[:5])
print("===================================================================")
print(tags[:5])
print("===================================================================")
```
- 查看dataframe的summary
```
users.info()
print("-----------------------------------")
ratings.info()
print("-----------------------------------")
movies.info()
print("-----------------------------------")
links.info()
print("-----------------------------------")
tags.info()
```

## 2.3 根据性别和年龄计算某部电影的平均得分
可用pandas.merge 将所有数据都合并到一个表中。merge有四种连接方式（默认为inner），分别为
- 内连接(inner)，取交集；
- 外连接(outer)，取并集，并用NaN填充；
- 左连接(left)，左侧DataFrame取全部，右侧DataFrame取部分；
- 右连接(right)，右侧DataFrame取全部，左侧DataFrame取部分；
```
data = pd.merge(pd.merge(ratings, users), movies)
data.info()
```
![](https://upload-images.jianshu.io/upload_images/16782311-89c7d21e8e8334f4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

通过索引器查看第一行数据，使用基于标签的索引.loc或基于位置的索引.iloc
![](https://upload-images.jianshu.io/upload_images/16782311-34ae26c3cb5bc4ad.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 2.4 按性别计算每部电影的平均得分
可通过数据透视表([pivot_table](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.pivot_table.html?highlight=pivot_table#pandas.DataFrame.pivot_table))实现

该操作产生了另一个DataFrame，输出内容为rating列的数据，行标index为电影名称，列标为性别，aggfunc参数为函数或函数列表（默认为numpy.mean），其中“columns”提供了一种额外的方法来分割数据。
![](https://upload-images.jianshu.io/upload_images/16782311-920db89ce7ae2147.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 2.5 过滤评分数据不够250条的电影
- 通过groupby()对title进行分组
- 利用size()得到一个含有各电影分组大小的Series对象
```
print("过滤评分数据不够250条的电影")
ratings_by_title = data.groupby('title').size()
print(ratings_by_title[:10])
```
![](https://upload-images.jianshu.io/upload_images/16782311-a47deb864167970c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 最后通过index索引筛选出评分数据大于250条的电影名称
```
print("通过index索引筛选出评分数据大于250条的电影名称")
active_titles = ratings_by_title.index[ratings_by_title >= 250]
print(active_titles)
```
![](https://upload-images.jianshu.io/upload_images/16782311-f5575e85def5071c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 使用mean_ratings选取所需的行
```
mean_ratings = mean_ratings.loc[active_titles]
mean_ratings.info()
print(mean_ratings[:5])
```
![](https://upload-images.jianshu.io/upload_images/16782311-e27371b6955b627a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 2.6 了解女性观众最喜欢的电影
- 通过[sort_index](http://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.sort_index.html?highlight=sort_index#pandas.DataFrame.sort_index)进行降序
```
top_female_ratings = mean_ratings.sort_index(by='F', ascending=False)
print(top_female_ratings[:10])
```
by参数的作用是针对特定的列进行排序（不能对行使用），ascending的作用是确定排序方式，默认为升序
![](https://upload-images.jianshu.io/upload_images/16782311-ac2bf24e8627dc28.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 2.7 计算评分分歧
增加一列存放平均得分之差，并对其排序，得到分歧最大且女性观众更喜欢的电影
```
mean_ratings['diff'] = mean_ratings['M'] - mean_ratings['F']
sorted_by_diff = mean_ratings.sort_index(by='diff')
print(sorted_by_diff[:10])
```
![](https://upload-images.jianshu.io/upload_images/16782311-fa8902a4f73b1497.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 对排序结果反序可得男性观众更喜欢的电影
![](https://upload-images.jianshu.io/upload_images/16782311-e24ba8e95e3cce58.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# 3 再处理
## 3.1  数据集整合
```
movie_ratings = pd.merge(movies, ratings)
lens = pd.merge(movie_ratings, users)
```
## 3.2  列出被评价过次数最多的20部电影
按照电影标题将数据集分为不同的groups，并且用size( )函数得到每部电影的个数（即每部电影被评论的次数），按照从大到小排序，取最大的前20部电影列出如下
```
most_rated = lens.groupby('title').size().sort_values(ascending=False)[:20]
print(most_rated)
```
![](https://upload-images.jianshu.io/upload_images/16782311-426d7c6cfa8ec48c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 3.3 评分最高的十部电影 
按照电影名称分组，用agg函数通过一个字典{‘rating’: [np.size, np.mean]}来按照key即rating这一列聚合，查看每一部电影被评论过的次数和被打的平均分。取出至少被评论过100次的电影按照平均评分从大到小排序，取最大的10部电影。
```
movie_stats = lens.groupby('title').agg({'rating': [np.size, np.mean]})
atleast_100 = movie_stats['rating']['size'] >= 100
print(movie_stats[atleast_100].sort_values([('rating', 'mean')], ascending=False)[:10])
```
![](https://upload-images.jianshu.io/upload_images/16782311-eadb21accfb21499.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 3.4 查看不同年龄见争议最大的电影
- 查看用户的年龄分布：
```
users.age.plot.hist(bins=30)
plt.title("Distribution of users' ages")
plt.ylabel('count of users')
plt.xlabel('age');
```
![](https://upload-images.jianshu.io/upload_images/16782311-d5bad3b37fa51579.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 用pandas.cut函数将用户年龄分组
```
labels = ['0-9', '10-19', '20-29', '30-39', '40-49', '50-59', '60-69', '70-79']
lens['age_group'] = pd.cut(lens.age, range(0, 81, 10), right=False, labels=labels)
lens[['age', 'age_group']].drop_duplicates()[:10]
```
![](https://upload-images.jianshu.io/upload_images/16782311-4248e43e36df4e22.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 每个年龄段用户评分人数和打分偏好，看起来年轻人更挑剔一点点
```
lens.groupby('age_group').agg({'rating': [np.size, np.mean]})
```
![](https://upload-images.jianshu.io/upload_images/16782311-d67f278dfd88c43d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 查看被评价过最多次的50部电影在不同年龄段之间的打分差异。并且用unstack函数将数据转换为一个表格，每一行为电影名称，每一列为年龄组，值为该年龄组的用户对该电影的平均评分。

## 3.5 不同性别间争议最大的电影 
```
lens.reset_index(inplace=True)
pivoted = lens.pivot_table(index=['movieId', 'title'],
                           columns=['gender'],
                           values='rating',
                           fill_value=0)
pivoted['diff'] = pivoted.M - pivoted.F
print(pivoted.head())
```
![](https://upload-images.jianshu.io/upload_images/16782311-1ea4e31bfe2f68c7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

```
pivoted.reset_index('movieId', inplace=True)
disagreements = pivoted[pivoted.movieId.isin(most_50.index)]['diff']
disagreements.sort_values().plot(kind='barh', figsize=[9, 15])
plt.title('Male vs. Female Avg. Ratings\n(Difference > 0 = Favored by Men)')
plt.ylabel('Title')
plt.xlabel('Average Rating Difference')
plt.show()
```
![](https://upload-images.jianshu.io/upload_images/16782311-c9528d08802639fc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


# X 交流学习
![](https://img-blog.csdnimg.cn/20190504005601174.jpg)
## [Java交流群](https://jq.qq.com/?_wv=1027&k=5UB4P1T)
![](https://img-blog.csdnimg.cn/20190502142519844.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzMzNTg5NTEw,size_16,color_FFFFFF,t_70)

## [博客](http://www.shishusheng.com)

![](https://img-blog.csdnimg.cn/20190502142541289.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzMzNTg5NTEw,size_16,color_FFFFFF,t_70)

## [Github](https://github.com/Wasabi1234)
