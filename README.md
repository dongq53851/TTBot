![ttbot](accessory/logo.png) 

使用今日头条web版API实现的头条机器人，涵盖账密登陆、滑动验证、关注与粉丝操作、头条号内容操作，
转发评论等。支持定时器任务，实现预定的用户互动，又可以作为头条新闻文章爬虫，采集相关资讯存储。
默认使用 **MongoDB** 数据库进行存储

## 更新历史
* 2020/02/27 对登陆滑动以及搜索滑动进行修复，登陆滑动的微调参数在`config.py`中设置`SLIDER_DEBUG`（其他有时间再改.）

----------
## 目录
- [项目结构](#h2-id1h2)
- [使用文档](#h2-id2h2)
  * [安装使用环境(**requirements.txt**)](#h3-id200-requirementstxth3)
  * [安装MongoDB数据库](#h3-id211-mongodbh3)
  * [chromedriver版本下载](#h3-id222-chromedriverh3)
  * [账密登陆](#h3-id233-h3)
  * [头条搜索(关键词综合、视频、用户搜索)](#h3-id244-h3)
  * [ 🚀 新闻爬取(45类新闻获取)](#h3-id255-h3)
  * [ 🚀 头条用户信息采集（无需登录）](#h3-id266-h3)
    * [x] [获取用户头像、id、粉丝数、关注数](#使用文档)
    * [x] [获取用户发布的所有/指定数量 的文章、视频、微头条](#使用文档)
    * [x] [获取用户关注列表的所有/指定数量 的头条账户的信息](#使用文档)
    * [x] [获取用户的粉丝列表 的头条账户信息](#使用文档)
  * [ 🚀 用户链式采集](#使用文档)
  * [ 🚀 登陆用户操作（需登录）](#使用文档)
     * [x] [获取账户基本信息、状态](#使用文档)
     * [x] [关注某个头条用户](#使用文档)
     * [x] [取消关注某个头条用户](#使用文档)
     * [x] [按照筛选条件关注用户列表](#使用文档)
     * [x] [按照筛选条件取消关注用户列表](#使用文档)
     * [x] [按照筛选条件关注某个用户的关注列表](#使用文档)
     * [x] [按照筛选条件取消关注某个用户的关注列表](#使用文档)
     * [x] [发微头条（图文皆可）](#使用文档)
     * [x] [发布头条号图文作品](#使用文档)
     * [x] [评论某个头条文章、视频、微头条](#使用文档)
     * [x] [获取某个头条媒体的可见评论](#使用文档)
     * [x] [回复某个文章、视频、微头条下的某条评论](#使用文档)
     * [x] [发布悟空问答问题（图文描述皆可）](#使用文档)
     * [x] [转发并评论某个文章、视频、微头条](#使用文档)
     * [x] [删除自己发布的某条文章、视频、微头条](#使用文档)
     * [x] [删除自己头条号发布的图文作品](#使用文档)
     * [x] [根据筛选条件删除头条号发布的图文作品](#使用文档)
     * [x] [删除悟空问答中的草稿](#使用文档)
     * [x] [删除悟空问答问题](#使用文档)
     * [x] [删除头条号素材库中的图片](#使用文档)
     * [x] [收藏某个文章、视频、微头条](#使用文档)
     * [x] [取消收藏某个文章、视频、微头条](#使用文档)
     * [x] [拉黑某个用户](#使用文档)
     * [x] [取消拉黑某个用户](#使用文档)
     * [x] [点赞某条评论](#使用文档)
     * [x] [取消点赞某条评论](#使用文档)
     * [x] [置顶某个头条文章作品](#使用文档)
     * [x] [取消置顶某个头条文章作品](#使用文档)
     * [x] [从主页中撤回某个图文作品](#使用文档)
     * [x] [恢复已撤回的某个图文作品到主页上](#使用文档)
     * [x] [头条素材库中收藏标记某张图片](#使用文档)
     * [x] [头条素材库中取消收藏标记某张图片](#使用文档)
     * [x] [获取关注列表用户](#使用文档)
     * [x] [获取粉丝列表用户](#使用文档)
     * [x] [获取头条通知、未读消息、问答邀请](#使用文档)
     * [x] [获取拉黑用户列表](#使用文档)
     * [x] [获取头条号订阅者列表](#使用文档)
     * [x] [获取我的收藏列表](#使用文档)
     * [x] [获取账户悟空问答草稿列表](#使用文档)
     * [x] [获取发布的所有/指定数量 的微头条、转发](#使用文档)
     * [x] [获取发布的所有/指定数量 的视频](#使用文档)
     * [x] [获取发布的所有/指定数量 的图文作品](#使用文档)
     * [x] [获取互动粉丝排行榜](#使用文档)
     * [x] [获取头条号素材库图片](#使用文档)
     * [x] [获取账户登陆操作日志](#使用文档)
     * [x] [获取账户敏感操作日志](#使用文档)
     * [x] [上传图片至头条号素材库](#使用文档)
     * [x] [小视频状态趋势数据](#使用文档)
     * [x] [悟空问答状态趋势数据](#使用文档)
     * [x] [粉丝增长趋势数据](#使用文档)
     * [x] [发布作品的概况趋势数据](#使用文档)
     * [x] **❤🚀 [与一些用户进行交互](#使用文档)**
  * [ 🚀 定时器](#使用文档)
     * [定时器使用](#使用文档)
     * [编写定时器任务](#使用文档)
- [后续TODO](##后续TODO)
- [赞助支持](##赞助支持)
- [学习交流](##学习交流)
  - 公众号
  - QQ群
- [免责声明](##免责声明)

## <h2 id='1'>项目结构</h2>
```
│  config.py             #项目配置文件
│  README.md
│  requirements.txt      #第三方依赖包
│  settings.py           #项目基础设置
├─ accessory                   
│      chromedriver
│      cookie.txt        #账户登陆cookie保存文件 
├─ component             #项目主体
│      account.py        #登陆账户操作类模块
│      dbhelper.py       #数据库模块
│      grabber.py        #新闻抓取执行类模块
│      log.py            #日志记录模块
│      news.py           #头条新闻类模块
│      search.py         #头条搜索模块
│      sliderlogin.py    #滑动验证登陆模块   
│      timer.py          #定时器模块
│      toutiao.py        #TTbot类模块
│      user.py           #头条用户类模块
├─ deco                  #component中各个模块的装饰器
│      crawl.py
│      login.py
│      toutiao.py
│      user.py
├─ img                   #滑动验证图片保存文件夹
├─ javascript            #js解密需要JavaScript文件
│      ascp.js          
│      signature.js
│      tasessionID.
├─ log                   #项目日志保存文件夹
└─ util                  #项目工具函数类，对应各个模块
        account.py
        jstool.py
        news.py
        proxy.py
        request.py
        search.py
        slider.py
        thread.py
        tools.py
        user.py
```
## <h2 id='2'>使用文档</h2>
> 以下所有的数据采集均默认使用**MongoDB**数据库进行保存

### <h3 id='2.0'>0. 安装使用环境(requirements.txt)</h3>
安装项目需要的第三方模块，在确保本机安装的python版本为3.x后，使用命令行:
```commandline
pip install -r requirements.txt
```
###  <h3 id='2.1'>1. 安装MongoDB数据库</h3>
> * [Windows 平台安装 MongoDB](https://www.runoob.com/mongodb/mongodb-window-install.html)
> * [Linux平台安装MongoDB](https://www.runoob.com/mongodb/mongodb-linux-install.html)
> * [Mac OSX 平台安装 MongoDB](https://www.runoob.com/mongodb/mongodb-osx-install.html)

Python 要连接 MongoDB 需要 MongoDB 驱动，这里我们使用 PyMongo 驱动来连接，安装pymongo(requirement.txt已经包含),
若自行安装，使用命令行:
```commandline
pip install pymongo
```
###  <h3 id='2.2'>2. chromedriver版本下载</h3>
项目使用的selenium驱动浏览器为Chrome，需要根据本机的Chrome版本来下载对应的chromedriver,
Chrome浏览器版本及其Chromedriver对应版本可以参照:

> [chromedriver与chrome各版本及下载地址](https://blog.csdn.net/cz9025/article/details/70160273)

下载成功后将chromedriver.exe放置于项目accessory文件夹下替换原先的chromedriver.exe，并在config.py中检查 
<font color=red>**CHROME_PATH**</font>  路径是否正确。

###  <h3 id='2.3'>3. 账密登陆</h3>
项目登陆使用的是账户密码模式的登陆，登陆方式有以下3种:
* 在config.py中设置好 账户密码:
```python
USERNAME = '账户'
PASSWORD = '密码'
```
代码使用:
```python
from component.toutiao import TTBot

bot = TTBot()
account = bot.account
account.login()
```
* 直接传入账户密码
```python
from component.toutiao import TTBot

bot = TTBot()
account = bot.account
account.login(username='账户',password='密码')
```
* 使用cookie登陆
在config.py 中设置账户cookie：
```python
COOKIE = 'tt_web_id=xxxxx;sso_user=xxxx'
```
而后使用第一种方式代码登陆。
> 账户登陆需要用到selenium模拟滑动验证，请确保已经下载好Chrome浏览器对应版本的chromedriver.exe

###  <h3 id='2.4'>4. 头条搜索(关键词综合、视频、用户搜索)</h3>
搜索模式一共有三种：
> * [综合搜索](####综合搜索)
> * [视频搜索](####视频搜索)
> * [用户搜索](####用户搜索)

第一次搜索需要进行滑动验证，需要使用selenium进行模拟验证。
 * #### 综合搜索
   
一般搜索结果为文章类，默认模式即为综合搜索:
```python
from component.toutiao import TTBot

bot = TTBot()
# 搜索 关键词 Gucci 的文章类头条结果，ALL置真表示获取所有结果，MDB置真表示使用数据库保存
results_all = bot.search('Gucci',ALL=True,MDB=True)
# 搜索 关键词 Gucci 的文章类头条结果，ALL置False,count=100表示只获取100条结果，MDB置真表示使用数据库保存
results_100 = bot.search('Gucci',ALL=False,MDB=True,count=100)
# 登陆后再进行搜索，不进行数据库保存
results_login = bot.search('Gucci',ALL=True,login=True)
```
综合搜索返回的单条数据示例:
```
```

 * #### 视频搜索
 示例代码：
 ```python
from component.toutiao import TTBot

bot = TTBot()

# 搜索 关键词 java 的视频类头条结果，ALL置真表示获取所有结果，MDB置真表示使用数据库保存
results = bot.search('java',VIDEO=True,MDB=True,ALL=True)
# 搜索 关键词 java 的视频类头条结果，ALL置False,count=100表示只获取100条结果，MDB置真表示使用数据库保存
results_100 = bot.search('java',ALL=False,MDB=True,count=100)
```
视频搜索返回的单条数据示例:

  * #### 用户搜索
 示例代码：
```python
from component.toutiao import TTBot

bot = TTBot()

# 搜索 名称中有 java 的头条用户，ALL置真表示获取所有结果，MDB置真表示使用数据库保存
results = bot.search('java',USER=True,MDB=True,ALL=True)
# 搜索 名称中有 java 的头条用户，ALL置False,count=100表示只获取100条结果，MDB置真表示使用数据库保存
results_100 = bot.search('java',USER=True,ALL=False,MDB=True,count=100)
# strict置真表示只搜索匹配 名称为 java 的头条用户,返回结果为匹配用户或None
results_strict = bot.search('java',strict=True,USER=True)
```
用户搜索返回的单条数据示例(strict=False情况下):
 
###  <h3 id='2.5'>5. 新闻爬取</h3>
头条新闻的采集（无需登陆）可以分为45个类别的新闻，包括首页推荐、热点、科技、军事、美食、历史等，具体可以查看
`component.news`模块的`TTNews`类源码。
示例代码:
```python
from component.toutiao import TTBot

bot = TTBot()
# 新闻爬虫
spider = bot.news_spider

#获取首页推荐新闻,ALL置真表示获取所有，MDB置真表示存入数据库
recommend_news = spider.get_recommend_news(ALL=True,MDB=True)
#获取首页推荐新闻,ALL置False,count=100表示只获取前100条数据，MDB置真表示存入数据库
recommend_100 = spider.get_recommend_news(ALL=False,count=100,MDB=True)
#获取 2019-07-07 12:00:00 以后的所有 首页推荐新闻，时间之前的数据忽略
recommend_by_dtime = spider.get_recommend_news(ALL=True,MDB=True,last_time='2019-07-07 12:00:00')

# --类似的API接口可以查看 TTNews 类的源码--

# 热点新闻获取
hot_news = spider.get_hot_news(MDB=True)
# 娱乐新闻
entertaining_news = spider.get_entertainment_news(MDB=True)
# 军事新闻
military_news = spider.get_military_news(MDB=True)
# 游戏新闻
game_news = spider.get_game_news(MDB=True)
# 财经新闻
financial_news = spider.get_finance_news(MDB=True)
# 投资新闻
investment_news = spider.get_investment_news(MDB=True)
# 美食新闻
food_news = spider.get_food_news(MDB=True)
...
```
新闻采集返回的单条数据示例（热点新闻为例）:

###  <h3 id='2.6'>6. 头条用户信息采集（无需登录）</h3>

一共有以下几个方面:
> * [获取用户基本信息](####获取用户基本信息)
> * [获取用户关注列表](####获取用户关注列表)
> * [获取用户粉丝列表](####获取用户粉丝列表)
> * [获取用户发布的文章](#h4-id262h4)
> * [获取用户发布的视频](####获取用户发布的视频)
> * [获取用户发布的微头条](####获取用户发布的微头条)

针对某个头条用户，我们需要获取到ta的相关信息，只需要知道其`uid`即可，即访问其头条首页，
可以查看到用户的地址url类似：`https://www.toutiao.com/c/user/3564799576/`，
那么`3564799576`即是用户的`uid`。

 * #### 获取用户基本信息
示例代码：
```python
from component.user import TTUser

user = TTUser('5787290902')
# 用户基本信息
info = user.info
```
返回结果：

* #### 获取用户关注列表
示例代码：
```python
from component.user import TTUser

user = TTUser('5787290902')
#获取用户的所有关注用户并存入数据库
followings = user.get_followings(MDB=True)
# 获取用户的前100个关注用户并存入数据库
followings_100 = user.get_followings(MDB=True,count=100)
```

返回的单个关注用户数据示例：

* #### 获取用户粉丝列表
示例代码：
```python
from component.user import TTUser

user = TTUser('5787290902')
# 获取用户的可见粉丝并存入数据库
fans = user.get_fans(MDB=True)
# 获取用户的前100个粉丝并存入数据库
fans_100 = user.get_fans(count=100,MDB=True)
```
返回的单个粉丝数据示例：

* #### <h4 id='2.6.2'>获取用户发布的文章</h4>
获取用户发布的媒体数据，用到的是`component.user`模块中的`TTUser`类method`get_published`,该函数不仅可以获取到
用户的媒体数据，还可以对每一次获取到的数据列表中的单条数据进行回调处理，可以传入参数`data_cb`、`cb_args`进行回调函数及其参数的
设置。

示例代码：
```python
from component.user import TTUser

user = TTUser('5787290902')
# 获取用户发布的所有文章并存储
articles = user.get_published(ALL=True,MDB=True)
# 获取用户发布的100条文章数据并存储
articles_100 = user.get_published(count=100,ALL=False,MDB=True)
```
采集到的用户文章`单条数据`示例：

使用回调函数对每一次获取到的数据集进行 `单条数据` 的处理:
```python
from component.user import TTUser

user = TTUser('5787290902')

def print_data(data_item,sec_param):
    '''
    回调函数的第一个参数永远都是 获取到的单条json数据 get_published函数
    已经默认传入，所以在 cb_args 中需要传入的参数 只能从第二个参数开始
    当前函数 的 sec_param 值为:'This is the sec param' 即为cb_args
    的第一个值。
    返回值提醒:
        返回 None:回调函数处理后继续进行后续的数据库保存、格式清理等工作
        返回 True:回调函数处理后 忽略此条数据，进行下一条数据的获取处理
    '''
    print(data_item,sec_param)

# 对单条数据使用print_data回调函数处理
articles = user.get_published(count=100,MDB=True,data_cb=print_data,cb_args=('This is the sec param',))

#使用lambda 来表示上面的 回调处理
results =  user.get_published(count=100,MDB=True,data_cb=lambda x,y:print(x,y),cb_args=('This is the sec param',))
```
* #### 获取用户发布的视频

获取视频数据，对单条视频json数据进行处理的回调操作与 获取文章数据回调处理是一样的,详见[`获取用户发布的文章`](#h4-id262h4)

示例代码：
```python
from component.user import TTUser
from settings import VIDEO

user = TTUser('5787290902')
# 获取用户发布的所有视频并存储
videos = user.get_published(MODE=VIDEO,ALL=True,MDB=True)
# 获取用户发布的100条视频数据并存储
videos_100 = user.get_published(MODE=VIDEO,count=100,MDB=True)
```
采集到的用户视频`单条数据`示例：
```

* #### 获取用户发布的微头条

获取微头条数据，对单条微头条json数据进行处理的回调操作与 获取文章数据回调处理是一样的,详见[`获取用户发布的文章`](#h4-id262h4)
示例代码：
```python
from component.user import TTUser
from settings import WEITT

user = TTUser('5787290902')
# 获取用户发布的所有微头条并存储
weitt = user.get_published(MODE=WEITT,ALL=True,MDB=True)
# 获取用户发布的100条微头条数据并存储
weitt_100 = user.get_published(MODE=WEITT,count=100,MDB=True)
```
采集到的用户微头条`单条数据`示例：


### <h3 id='2.7'>7. 用户链式采集</h3>

当我们需要大量的头条用户发布数据进行数据分析时，我们可以使用用户链式爬取来采集数据，存入数据库。
只需要提供一个入口用户`ENTER_USER_ID`给爬虫，便可以一键采集，可以在`config.py`中设置入口用户。
主要用到的函数为`component.toutiao`模块中类`TTBot`的`grab_all_user_posts`(可以查看该类函数源码注释)。具体的采集逻辑：

![grabber](accessory/grab.png)

示例代码:
```python
from component.toutiao import TTBot
from settings import ARTICLE,VIDEO,WEITT
bot = TTBot()

# 链式爬取用户的所有发布数据，包括文章、视频、微头条
bot.grab_all_user_posts('all')
# 链式爬取用户的所有文章数据
bot.grab_all_user_posts(ARTICLE)
# 链式爬取用户的所有视频数据
bot.grab_all_user_posts(VIDEO)
# 链式爬取用户的所有微头条数据
bot.grab_all_user_posts(WEITT)
```
所有的返回爬取数据均可在数据库中查看，对应的数据库名称可以查看`config.py`中的数据库设置。
采集单条数据示例与[头条用户信息采集（无需登录）](#h3-id266-h3)的一致。

### <h3 id='2.8'>8. 登录用户操作</h3>

有些操作需要登录头条账户才能进行操作，如：关注用户、发布头条图文等。需要先进行[`账密登录`](#h3-id233-h3)设置。

> 提示：以下内容均默认已在`config.py`中设置好`账户密码`。
>
后续操作示例代码中的 `account` 为以下代码变量：
```python
from component.toutiao import TTBot
bot = TTBot()
account = bot.account
``` 

* #### 获取账户基本信息、状态

示例代码：
```python
# 账户基本信息
user_info = account.user_info
# 账户头条媒体信息
media_info = account.media_info
# 账户 头条状态 
status = account.account_status
```
返回数据示例:

* #### 关注某个头条用户

示例代码：
```python
# 关注 头条uid为4492956276的用户 （央视新闻）
result = account.follow_user('4492956276')
```
返回结果示例：
```json5
{'message': 'success', 'data': {}}
```

* #### 取消关注某个头条用户

示例代码：
```python
# 取消关注 头条uid为4492956276的用户 （央视新闻）
result = account.unfollow_user('4492956276')
```
返回结果示例：
```json5
{'message': 'success', 'data': {}}
```
* #### 按照筛选条件关注用户列表

给定一个用户uid列表，按照自己筛选条件需求进行关注操作。

示例代码：
```python
# 按照筛选条件关注用户列表  uids:[]
uids = ['50502346173','4377795668','3640241275']
# 关注列表中的所有用户
account.follow_users(uids)
# 关注列表中 粉丝数不为0 的用户
account.follow_users(uids,skip_no_fans=True)
# 关注列表中 关注数不为0 的用户
account.follow_users(uids,skip_no_followings=True)
# 关注列表中 发布文章数不为0 的用户
account.follow_users(uids,no_articles=True)
# 关注列表中 发布视频数不为0 的用户
account.follow_users(uids,no_videos=True)
# 关注列表中 发布微头条数不为0 的用户
account.follow_users(uids,no_weitt=True)
# 关注列表中 发布微头条数不为0、粉丝数不为0 的用户
account.follow_users(uids,no_weitt=True,skip_no_fans=True)
```
* #### 按照筛选条件取消关注用户列表

给定一个用户uid列表，按照自己筛选条件需求进行取消关注操作。

示例代码：
```python
# 按照筛选条件取消关注用户列表  uids:[]
uids = ['50502346173','4377795668','3640241275']
# 取消关注列表中的所有用户
account.unfollow_users(uids)
# 取消关注列表中 粉丝数为0 的用户
account.unfollow_users(uids,only_no_fans=True)
# 取消关注列表中 关注数为0 的用户
account.unfollow_users(uids,only_no_followings=True)
# 取消关注列表中 发布文章数为0 的用户
account.unfollow_users(uids,no_articles=True)
# 取消关注列表中 发布视频数为0 的用户
account.unfollow_users(uids,no_videos=True)
# 取消关注列表中 发布微头条数为0 的用户
account.unfollow_users(uids,no_weitt=True)
# 取消关注列表中 发布微头条数为0、粉丝数为0 的用户
account.unfollow_users(uids,no_weitt=True,skip_no_fans=True)
```

* #### 按照筛选条件关注某个用户的关注列表

给定一个用户uid，对其关注列表根据自己需求筛选条件进行关注操作。

示例代码：
```python
uid = '4377795668'
# 关注用户关注列表中的所有用户，参数ALL默认为True，表示默认获取所有用户关注的账户
account.follow_followings_of_user(uid)
# 关注用户关注列表中的 粉丝数不为0 的所有用户
account.follow_followings_of_user(uid,skip_no_fans=True)
# 关注用户关注列表中的 关注数不为0 的所有用户
account.follow_followings_of_user(uid,skip_no_followings=True)
# 关注用户关注列表中的 发布文章数不为0 的所有用户
account.follow_followings_of_user(uid,no_articles=True)
# 关注用户关注列表中的 发布视频数不为0 的所有用户
account.follow_followings_of_user(uid,no_videos=True)
# 关注用户关注列表中的 发布微头条数不为0 的所有用户
account.follow_followings_of_user(uid,no_weitt=True)
# 关注用户关注列表中的 发布文章数不为0 的前 20 个用户
account.follow_followings_of_user(uid,no_articles=True,count=20,ALL=False)
```

* #### 按照筛选条件取消关注某个用户的关注列表

给定一个用户uid，对其关注列表根据自己需求筛选条件进行取消关注操作。

示例代码：
```python
uid = '4377795668'
# 取消关注用户关注列表中的所有用户，参数ALL默认为True，表示默认获取所有用户关注的账户
account.unfollow_followings_of_user(uid)
# 取消关注用户关注列表中的 粉丝数为0 的所有用户
account.unfollow_followings_of_user(uid,only_no_fans=True)
# 取消关注用户关注列表中的 关注数为0 的所有用户
account.unfollow_followings_of_user(uid,only_no_followings=True)
# 取消关注用户关注列表中的 发布文章数为0 的所有用户
account.unfollow_followings_of_user(uid,no_articles=True)
# 取消关注用户关注列表中的 发布视频数为0 的所有用户
account.unfollow_followings_of_user(uid,no_videos=True)
# 取消关注用户关注列表中的 发布微头条数为0 的所有用户
account.unfollow_followings_of_user(uid,no_weitt=True)
# 取消关注用户关注列表中的 发布文章数为0 的前 20 个用户
account.unfollow_followings_of_user(uid,no_articles=True,count=20,ALL=False)
```

* #### 发微头条（图文皆可）

示例代码：
```python
# 如果微头条有图片，可以传入图片参数
# 多于一张的需用list列表传入
image_path = r'C://pictures/test.jpg'
image_list = [r'C://pictures/test01.jpg',r'C://pictures/test02.jpg']
weitt_content = '这是一个测试用微头条.[posted by TTBot]'
# 发布内容中只有一张图片
account.post_weitt(weitt_content,image=image_path)
# 发布内容中包含有两种或以上的图片
account.post_weitt(weitt_content,image=image_list)
```
返回结果数据示例：
```json5
{'message': 'success', 'data': {'open_url': '/group/1638551478768651/', 'group_id': 1638551478768651}}
```

* #### 发布头条号图文作品

头条的图文作品可以获得收益，关键在于阅读量点击量等有效参数，发布的图片作品归档于文章中。

示例代码：
```python
cover_image_path = r'C://pictures/test.jpg'
cover_image_url = 'https://www.picture.com/test.jpg'
title = '头条测试作品，字数需大于5个字符'
content = '这是一篇头条图文作品的内容。<strong>可以是富文本。</strong>但不能包含img标签'

# 发布 不含封面的图文作品 默认投放头条广告 run_ad=True
account.post_article(title,content)
#  不投放头条广告
account.post_article(title,content,run_ad=False)
# 加入封面图片,使用本地图片上传
account.post_article(title,content,cover_img=cover_image_path)
# 加入封面图片,使用网络图片地址
account.post_article(title,content,cover_img=cover_image_url)
# 定时发布图文作品  格式：2019-07-09 12:10:10
account.post_article(title,content,timer_time='2019-07-09 12:10:10')
# 使用扩展链接
account.post_article(title,content,extern_link='https://somewebsite.com')
# 发布的图文作品 参加 新写作大赛 的模式： 0:不参加 1:参加主竞赛单元评选 2:参加青年竞赛单元评选
account.post_article(title,content,writting_race_mode=1)
```
返回结果数据示例:
```json5
{'message': '提交成功', 'code': 0, 'data': {'pgc_id': '6711509552061219331'}}
```

* #### 评论某个头条文章、视频、微头条

在知道某个头条发布媒体(文章、视频、微头条)的id后，直接发布评论。重复评论只算一个。

如何知道用户文章、视频、微头条id？查看其链接如：`https://www.toutiao.com/i6711548842266853892/`
则 `6711548842266853892` 为该媒体id。

示例代码：
```python
media_id = '6711548842266853892'
comment_content = '这是一个测试评论'

account.post_comment(comment_content,media_id)
```
返回的结果数据示例：
```json5
{
    'comment':
    {
        'status': 7,
        'text': '这是一个测试评论',
        'create_time': '2019-07-09 16:58:09',
        'user_id': 95480041731, 
        'id': 6711585125912084488,
    }, 
    'message': 'success', 
    'created': true,
    }
```

* #### 获取某个头条媒体的可见评论

示例代码
```python
# 获取头条文章(https://www.toutiao.com/i6689315272605565452/)的可见评论
comments = account.get_comments_of_media('6689315272605565452')
```
返回的数据示例:
```json5
{
    'message': 'success',
    'data': 
    {
        'has_more': false, 
        'total': 10, 
        'comments': [
            {
                'text': '确认过眼神，阿里是干大事的', 
                'digg_count': 3,
                'reply_data': {'reply_list': []},
                'reply_count': 0,
                'create_time': 1557494219, 
                'user': 
                {
                    'avatar_url': 'https://p9.pstatp.com/thumb/5d480005d11a693b87ef', 
                    'user_id': 86931246069, 
                    'name': 'Joshua2014',
                }, 
                'dongtai_id': '6689386720494043147',
                'user_digg': 0,
                'id': '6689386720494043147',
            },
        ],
    },
}
```

* #### 回复某个文章、视频、微头条下的某条评论

回复上述头条文章获取到的可见评论中的第一条评论。

示例代码：
```python
# 参考上述的返回评论数据示例，可以获得相关的必须参数
item_id = '6689315272605565452'
comment_id = '6689386720494043147'
reply_text = '这是一个测试回复'
reply_to_user_id = '86931246069'
# 发表评论回复 
account.post_reply(reply_text,item_id,comment_id,reply_to_user_id)
```
返回的json数据:
```json5
{
    'message': 'success',
    'data': 
    {
        'comment': 
        {
            'is_pgc_author': false,
            'is_owner': false,
            'text': '这是一个测试回复',
            'content': '这是一个测试回复',
            'create_time': 1562680661,
            'reply_id': 0,
            'user': 
            {
                'verified_reason': '', 
                'screen_name': '贩卖咸鱼的木木', 
                'avatar_url': 'http://p1.pstatp.com/thumb/b724000372257b2b92aa',
                'user_id': 95480041731, 
                'name': '贩卖咸鱼的木木', 
                'author_badge': [], 
                'user_auth_info': '', 
                'user_verified': false, 
                'description': '说出你要的视频哟~~！！',
            },
            'id': 6711662322362318860, // 此条回复的id
        }, 
        'comment_id': 6689386720494043147, // 回复的评论id
    },
}

```

* #### 发布悟空问答问题（图文描述皆可）

示例代码:
```python
title = '这是一个测试的悟空问答 问题'
content = '这是问题的具体描述'
image = r'C://pictures/test.jpg'
image_list = [r'C://pictures/test01.jpg',r'C://pictures/test02.jpg']

# 发表悟空问答 并附上本地图片一张
account.post_question(title,content,image)
# 发表悟空问答 并附上本地图片多张，使用列表
account.post_question(title,content,image_list)
```

返回的结果数据示例:
```json5
{'qid': '6711665324736905475', 'err_no': 0, 'err_tips': ''}
```

* #### 转发并评论某个文章、视频、微头条

示例代码:
```python
# 转发 用户 阿里达摩院扫地僧（uid:6636211626）的文章（id:6689315272605565452）
repost_content = '转发并评论的内容'
uid = '6636211626'
item_id = '6689315272605565452'
# 转发并评论
account.repost(repost_content,item_id,uid)
```
返回的结果数据示例:
```json5
{
    'message': 'success', 
    'data': 
    {
        'open_url': '/group/6711667304335802382/', 
        'group_id': 6711667304335802382,
    },
}
```
* #### 删除自己发布的某条文章、视频、微头条

示例代码:
```python
# 删除 上一项 自己发布的一个转发并评论 阿里达摩院扫地 的微头条,
# comment=True 表示此条微头条属于转发类型，如果属于转发类型的微头条，
# 删除时必须指定 comment=True
account.delete_media('6711667304335802382',comment=True)
# 如果是一般自己发布的图文微头条，则不用传入comment的值
account.delete_media('1638551478768651')
# 如果需要删除的是自己发布的小视频，则需使用 delete_video 函数,传入该小视频 id即可
account.delete_video('6711667304335802382')
```
返回数据示例:
```json5
{'message': 'success'}
```
* #### 删除自己头条号发布的图文作品

示例代码:
```python
# 删除一个自己发布的头条图文作品需要知道该图文文章的 id 
item_id = '6709615853203096071'
account.delete_article(item_id)
```
返回的数据示例:
```json5
{'code': 0, 'message': 'success', 'data': null}
```

* #### 根据筛选条件删除头条号发布的图文作品

头条号图文作品的发布状态有五种：`已发表`、`未通过`、`审核中`、`已撤回`、`草稿`。

对应的传入参数为:`passed`、`unpassed`、`checking`、`hide`、`draft`

可以根据`作品关键词`、`开始时间`、`结束时间`来搜索删除相关的图文作品

示例代码：
```python
# 删除 自己图文作品中 未通过审核的 所有作品
account.delete_articles(status='unpassed')
# 删除 自己图文作品中 通过审核的 且 包含关键词 “测试”、发布时间 位于 2019-07-01 至 2019-07-03 的所有作品
account.delete_articles(status='passed',keyword='测试',start_date='2019-07-01',end_date='2019-07-03')
```

* #### 删除悟空问答中的草稿

示例代码:
```python
# 需要传入 问题id
account.delete_wenda_draft('6711665324736905475')
```
返回结果数据示例:
```json5
{'err_no': 0, 'err_tips': ''}
```
* #### 删除悟空问答问题

能进行删除操作的悟空问答问题只能是处于`审核状态`中的提问。

示例代码:
```python
# 需要传入 问题id
account.delete_question('6706694894238302478')
```

返回结果示例:
```json5
// 问题审核中 已经删除
{'qid': '6711866197685567758', 'err_no': 0, 'err_tips': ''}
// 问题已过审核无法删除
{'qid': '6706694894238302478', 'err_no': 65546, 'err_tips': '问题状态不符合操作条件'}
```

* #### 删除头条号素材库中的图片

示例代码:
```python
# 需要传入 素材图片的uri 即 以pgc-image 的web_uri
account.delete_resource_img('pgc-image/266565ea60cb42c3a54b94ebdc58923a')
```
返回结果数据示例：
```json5
{'message': 'success', 'now': 1562742921, 'data': '', 'reason': ''}
```

* #### 收藏某个文章、视频、微头条

必须参数：该头条媒体（文章、视频、微头条）的 group_id

示例代码：
```python
account.store_media('6711635660941296132')
```
返回结果数据示例：
```json5
{'message': 'success'}
```

* #### 取消收藏某个文章、视频、微头条

必须参数：该头条媒体（文章、视频、微头条）的 group_id

示例代码：
```python
account.unstore_media('6711635660941296132')
```
返回结果数据示例：
```json5
{'message': 'success'}
```
* #### 拉黑某个用户

必须参数：需要拉黑的用户uid

示例代码:
```python
account.block_user('6681325527')
```
返回的结果数据示例：
```json5
{'message': 'success', 'now': 1562744234, 'data': '', 'reason': '拉黑成功！'}
```

* #### 取消拉黑某个用户

必须参数：需要取消拉黑的用户uid

示例代码:
```python
account.unblock_user('6681325527')
```
返回的结果数据示例：
```json5
{'message': 'success', 'now': 1562744303, 'data': '', 'reason': '取消拉黑成功！'}
```
* #### 点赞某条评论

必须参数：需要点赞的评论的id,mp平台仅能操作作者自己的文章相关的评论

示例代码:

```python
account.like_comment('6707339641345097735')
```
返回的结果数据示例：
```json5
{'message': 'success', 'now': 1562745148, 'data': '', 'reason': '点赞成功'}
```
* #### 取消点赞某条评论
必须参数：需要点赞的评论的id,mp平台仅能操作作者自己的文章相关的评论

示例代码:
```python
account.unlike_comment('6707339641345097735')
```
返回的结果数据示例：
```json5
{'message': 'success', 'now': 1562745323, 'data': '', 'reason': '取消点赞成功'}
```
* #### 置顶某个头条文章作品

必须参数：需置顶文章的id,文章创建时间戳 create_time

示例代码：
```python
account.set_top_article('6711941566493098504',create_time='1562745675')
```
返回的结果数据示例：
```json5
{'message': 'success', 'now': 1562746670, 'data': '', 'reason': '文章置顶成功'}
```
* #### 取消置顶某个头条文章作品

必须参数：需取消置顶文章的id,文章创建时间戳 create_time

示例代码：
```python
account.cancel_top_article('6711941566493098504',create_time='1562745675')
```
返回的结果数据示例：
```json5
{'message': 'success', 'now': 1562746748, 'data': '', 'reason': '文章取消置顶成功'}
```
* #### 从主页中撤回某个图文作品

必须参数：需要从主页中撤回（隐藏）的文章id

示例代码
```python
account.hide_article('6711941566493098504')
```
返回的结果数据示例：
```json5
{'code': 0, 'message': 'success', 'data': None}
```
* #### 恢复已撤回的某个图文作品到主页上

必须参数：需要从主页中恢复显示的文章id

示例代码：
```python
account.unhide_article('6711941566493098504')
```
返回的结果数据示例：
```json5
{'code': 0, 'message': 'success', 'data': None}
```
* #### 头条素材库中收藏标记某张图片

必须参数： 需要传入 素材图片的uri 即 以pgc-image 的web_uri

示例代码：
```python
account.star_resource_img('pgc-image/a8dc04c83f194adc9d0b56365e42fe50')
```
返回的结果数据示例：
```json5
{'message': 'success', 'now': 1562807025, 'data': '', 'reason': ''}
```
* #### 头条素材库中取消收藏标记某张图片
必须参数： 需要传入 素材图片的uri 即 以pgc-image 的web_uri

示例代码：
```python
account.unstar_resource_img('pgc-image/a8dc04c83f194adc9d0b56365e42fe50')
```
返回的结果数据示例：
```json5
{'message': 'success', 'now': 1562807115, 'data': '', 'reason': ''}
```
* #### 获取关注列表用户

默认存储进入MongoDB数据库。与无需登录的[头条用户信息采集（无需登录）](#h3-id266-h3) 获取用户关注列表一致

示例代码：
```python
# 获取所有的关注用户 并存入数据库
account.get_followings(ALL=True,MDB=True)
# 获取前100个关注用户 并存入数据库
account.get_followings(count=100,MDB=True)
```
返回的结果数据示例 与 [头条用户信息采集（无需登录）](#h3-id266-h3) 中`获取用户关注列表`获取到的单个用户json数据一致

* #### 获取粉丝列表用户

默认存储进入MongoDB数据库。与无需登录的[头条用户信息采集（无需登录）](#h3-id266-h3) 获取用户粉丝列表一致

示例代码
```python
# 获取所有的可见粉丝用户 并存入数据库
account.get_fans(ALL=True,MDB=True)
# 获取前100个粉丝用户 并存入数据库
account.get_fans(count=100,MDB=True)
```
返回的结果数据示例 与 [头条用户信息采集（无需登录）](#h3-id266-h3) 中`获取用户粉丝列表`获取到的单个用户json数据一致

* #### 获取头条通知、未读消息、问答邀请
示例代码：
```python
# 获取 头条媒体（文章、视频、微头条）相关评论通知数
media_noty = account.get_notification_count()
# 获取账户 新的粉丝数
unread_fans_count = account.get_unread_fans_count()
# 获取 得到的 问题邀请数
wenda_invited = account.get_wenda_invited_count()
```
返回的结果数据示例：
```json5
// media_noty  有相关的评论 微头条2个新的评论，文章有1个新的评论
{'video_pgc_count': 0, 'graphic_count': 1, 'wtt_count': 2}
```
```json5
// unread_fans_count  data 字段 1 表示有一个新的粉丝
{'message': 'success', 'now': 1562810209, 'data': 1, 'reason': ''}
```
```json5
// wenda_invited 表示收到4个问题邀请
{'invite_count': 4}
```
* #### 获取拉黑用户列表
示例代码：
```python
account.get_blocking_users()
```
返回的结果数据示例：
```json5
[
    {
        'avatar_url': 'http://p1.pstatp.com/thumb/6edc0005cd0d88147ac6',
        'user_id': 3784676286, 
        'name': '野史日记',
    }, 
    {
        'avatar_url': 'http://p1.pstatp.com/thumb/173b60001126f6279daa9', 
        'user_id': 104957058916, 
        'name': '旅行诗人安安',
    }, 
]
```
* #### 获取头条号订阅者列表

示例代码:
```python
# 获取所有的订阅者数据并存入数据库，数据库名称在 config.py 中MONGODB设置里的subscribers键值
account.get_subscribers(MDB=True)
# 获取100个订阅者数据并存入数据库，数据库名称在 config.py 中MONGODB设置里的subscribers键值
account.get_subscribers(count=100,MDB=True,ALL=False)
```
返回的结果数据示例：
```json5
[
    {
        'following': 1,  //是否你也关注了ta 1是 0否
        'avatar_url': 'http://p3.pstatp.com/thumb/fe480000747798606b4c', 
        'user_id': 54009707197, 
        'screen_name': '刺派',
    }, 
    {
        'following': 0, 
        'avatar_url': 'http://p1.pstatp.com/thumb/fe2c00002330aae7dbc5',
        'user_id': 4160017817,
        'screen_name': '水沐禅心34491537',
    }
]
```
* #### 获取我的收藏列表

示例代码：
```python
# 获取所有的收藏列表数据并存入数据库，数据库名称在 config.py 中MONGODB设置里的favourite键值
account.get_favourites(MDB=True)
# 获取100条收藏列表数据并存入数据库，数据库名称在 config.py 中MONGODB设置里的favourite键值
account.get_favourites(count=100,ALL=False,MDB=True)
```
返回的结果列表的单条json数据示例：
* #### 获取账户悟空问答草稿列表

示例代码：
```python
# 获取所有的悟空问答草稿箱数据并存入数据库，数据库名称在 config.py 中MONGODB设置里的wenda_draft键值
account.get_wenda_drafts(MDB=True)
# 获取100条悟空问答草稿箱数据并存入数据库，数据库名称在 config.py 中MONGODB设置里的wenda_draft键值
account.get_wenda_drafts(count=100,ALL=False,MDB=True)
```
返回的结果列表的单条json数据示例：
* #### 获取发布的所有/指定数量 的微头条、转发

示例代码：
```python
# 获取当前登陆用户所有的微头条、转发数据并存入数据库，数据库名称在 config.py 中MONGODB设置里的comments键值
account.get_posts(MDB=True)
# 获取100条当前登陆用户的微头条、转发数据并存入数据库，数据库名称在 config.py 中MONGODB设置里的comments键值
account.get_posts(count=100,ALL=False,MDB=True)
```
返回的结果列表的单条json数据示例：

* #### 获取发布的所有/指定数量 的视频

示例代码：
```python
# 获取当前登陆用户所有的小视频数据并存入数据库，数据库名称在 config.py 中MONGODB设置里的my_videos键值
account.get_videos(MDB=True)
# 获取100条当前登陆用户的小视频数据并存入数据库，数据库名称在 config.py 中MONGODB设置里的my_videos键值
account.get_videos(count=100,ALL=False,MDB=True)
```
返回的结果列表的单条json数据示例：

* #### 获取发布的所有/指定数量 的图文作品

图文作品的发布状态有五种：`已发表`、`未通过`、`审核中`、`已撤回`、`草稿`。

对应的传入参数为:`passed`、`unpassed`、`checking`、`hide`、`draft`

可以根据`作品关键词`(参数keyword)、`开始时间`(参数start_date)、`结束时间`(参数end_date)来搜索获取相关的图文作品

示例代码：
```python
# 获取当前登陆用户所有的图文作品数据并存入数据库，数据库名称在 config.py 中MONGODB设置里的my_articles键值
account.get_posted_articles(MDB=True)
# 获取100条当前登陆用户所有的图文作品数据并存入数据库，数据库名称在 config.py 中MONGODB设置里的my_articles键值
account.get_posted_articles(count=100,ALL=False,MDB=True)
# 获取100条当前登陆用户正在审核中的图文作品数据并存入数据库，数据库名称在 config.py 中MONGODB设置里的my_articles键值
account.get_posted_articles(count=100,ALL=False,MDB=True,status='checking')
# 获取100条当前登陆用户于 2019-07-01 至 2019-07-09 发布的正在审核中的 图文作品数据并存入数据库，数据库名称在 config.py 中MONGODB设置里的my_articles键值
account.get_posted_articles(count=100,ALL=False,MDB=True,status='checking',start_date='2019-07-01',end_date='2019-07-09')

# --- 对获取到的单条数据进行回调处理 参数：item_callbcak---
'''
想对爬取到的单条数据进行增删改字段等操作，可以使用回调函数：
假设想对获取到的每一条图文数据 打印其当前状态，可以使用自己定义一个回调函数如下（callback_print_status）:  
'''
def callback_print_status(account,item):
    ''' 
    第一个参数永远都是account，代表当前登陆账户，
    第二个参数表示的便是获取到的原始单条json数据 具体内容可以查看下面的数据示例
    返回：
        None 表示处理完后继续执行后续代码；
        1    表示处理完后忽略后续处理代码；
        元组(item,200) 表示用item替换原先的单条数据再继续后续代码处理
    '''
    print(item.get('status_desc'))

# 使用回调函数处理每一条数据 
account.get_posted_articles(item_callback=callback_print_status)
```
返回的结果列表的单条json数据示例：


* #### 获取互动粉丝排行榜

示例代码：
```python
#获取粉丝互动排行榜的第一页 数据的先后顺序表示了互动由高至低的排行
account.get_interact_fans(page=1)
```
返回的结果json数据示例：


* #### 获取头条号素材库图片
示例代码：
```python
# 获取素材库 全部图片 的 第二页 每页20条显示
account.get_resource_images(page=2,pagesize=20)
# 获取素材库 收藏图片 的 第一页 每页20条显示
account.get_resource_images(page=1,pagesize=20,saved=True)
```
返回的结果json数据示例：
```json5
{
    'message': 'success', 
    'now': 1562900747,
    'data': {
        'total_count': 77,  //素材库图片总数
        'resource_list': [
            {
                'create_time': 1562720147,  //上传时间
                'is_saved': false,  //当前图片是否是收藏图片
                'resource_id': 'pgc-image/a8dc04c83f194adc9d0b56365e42fe50',
            }
        ], 
        'page_index': 1,  //当前页码
        'page_size': 20,   //每页显示条数
    },
    'reason': '',
}
```
* #### 获取账户登陆操作日志

示例代码：
```python
# 获取账户登陆操作日志 的 第二页 每页20条显示
account.get_login_op_log(page=2,pagesize=20)
```
返回的结果json数据示例：
```json5
{
    'data': 
    {
        'op_log': [
            {
                'login_time': '2019-07-10T10:43:25+08:00', 
                'timestamp': 1562726605, 
                'ip_addr': '201.18.***.***',
                'device': '电脑', 
                'device_name': 'Windows', 
                'app_name': '今日头条(Web版)', 
                'login_method': '密码登录',
            }, 
        ],
    },
}
```
* #### 获取账户敏感操作日志

示例代码：
```python
# 获取账户敏感操作日志 的 第二页 每页20条显示
account.get_sensitive_op_log(page=2,pagesize=20)
```
返回的结果json数据示例：
```json5
{
    'data': 
    {
        'op_log': [
            {
                'op_time': '2018-09-17T18:43:28+08:00', 
                'timestamp': 1537181008,
                'ip_addr': '134.67.***.***', 
                'device': '电脑',
                 'device_name': 'Windows', 
                'action': '修改密码',
                'Action': 402,
            },
        ], 
        'total': 1,
    }, 
    'message': 'success',
}
```
* #### 上传图片至头条号素材库
示例代码：
```python
# 通过 本地图片上传
account.upload_resource_img_by_open(r'C://pictures/test.jpg')
# 通过 网络图片地址 上传
account.upload_resource_img_by_url('http://www.xxx.com/test.jpg')
```
返回结果数据示例：
```json5
{
    'message': 'success', 
    'data': {
            'url_list': [
            {'url': 'http://p3.pstatp.com/origin/242a500005c02321b60e8'},
            {'url': 'http://pb9.pstatp.com/origin/242a500005c02321b60e8'},
            {'url': 'http://pb1.pstatp.com/origin/242a500005c02321b60e8'}
        ],
        'web_uri': '242a500005c02321b60e8',
    },
}
```
* #### 小视频状态趋势数据
示例代码：
```python
# 获取'2019-07-01'至'2019-07-13'发布的小视频数据分析数据
account.small_videos_analysis('2019-07-01','2019-07-13')
```
返回的结果json数据示例：
```json5
{
    'err_no': 0, 
    'list': [
        {
            'id': '6712621136334553100',
            'href': 'http://toutiao.com/item/6712621136334553100/', 
            'title': 'test', 
            'play_count': 0,     //播放量
            'comment_count': 0,  //评论数
            'collect_count': 0,  //收藏数
            'forward_count': 0,  //转发数
            'average_progress': 0, //	平均进度
            'recommend_ratio': 0, 
            'follow_ratio': 0, 
        },
    ], 
    'message': 'success',
    'totalPage': 1,
}
```

* #### 悟空问答状态趋势数据

仅获取最近7天内的回答数据

示例代码：
```python
account.wenda_analysis()
```
返回的结果json数据示例：
```json5
{
    'message': 'success',
    'now': 1562904171, 
    'data':
    {
        'go_detail_count': 3, //阅读量
        'answer_count': 0, //回答数
        'digg_count': 1, //点赞数
    }, 
    'reason': '',
}
```
* #### 粉丝增长趋势数据
示例代码：
```python
#获取 2019-07-10至2019-07-12的 粉丝增长数据
account.get_fans_trend('2019-07-10','2019-07-12')
```
返回的结果json数据示例：
```json5
{
    'message': 'success', 
    'now': 1562904306, 
    'data': {
        'itemList': [
            {
                'date': '20190710', 
                'totalCount': 9,  //粉丝总数
                'incrCount': 0,   //增长数
                'decrCount': 0,   //减少数
                'netGrowthCount': 0, //净增长数
            }, 
            {
                'date': '20190711',
                'totalCount': 9,
                'incrCount': 0, 
                'decrCount': 0, 
                'netGrowthCount': 0,
            }
        ],
        'end_date': '2019-07-12',
        'start_date': '2019-07-10',
    },
    'reason': '',
}
```
* #### 发布作品的概况趋势数据
示例代码：
```python
#获取 2019-07-10至2019-07-12 发布作品的概况趋势数据
account.get_content_overview('2019-07-10','2019-07-12')
```
返回的结果json数据示例：
```json5
{
    'message': 'success', 
    'now': 1562904519, 
    'data': {
        'comment_count': 1,
        'surbscribe_go_detail_count': 0, 
        'go_detail_count': 11, //阅读量
        'end_date': '2019-07-11',
        'repin_count': 0,     //收藏量
        'detail_list': {
            // 列表的元素数对应天数       
            'surbscribe_go_detail_count': [0, 0], 
            'go_detail_count': [10, 1],
            'repin_count': [0, 0], 
            'impression_count': [1368, 270],
            'comment_count': [0, 1], 
            'share_count': [0, 0], 
            'publish_num': [0, 0],
        }, 
        'share_count': 0, //转发量
        'impression_count': 1638,  //推荐量总数
        'start_date': '2019-07-10',
        'publish_num': 5,
    }, 
    'reason': '',
}

```

* #### ❤ 与一些用户进行交互

目前只写了`与一些用户进行互动`的代码，具体为：给定一个用户uid列表，对列表中的用户指定日期范围或最近发布的文章、
视频、微头条进行指定条数的评论、转发的互动功能。

具体的参数解析可以查看`component.toutiao`模块的`interact_with_users`函数源码注释

示例代码：
```python
account.interact_with_users(
uids=['50025817786','6026436452'],  # 想要进行交互的用户uid列表
**{ 'comment_on_weitt':True,        # 是否对这些用户的微头条进行评论
    'comment_start_time':'2019-06-17 00:00:00', # 进行评论的用户头条媒体发布的开始时间范围
    'comment_end_time':'2019-06-18 00:00:00',  # 进行评论的用户头条媒体发布的结束时间范围
    'comment_on_video':True,    # 是否对这些用户的视频进行评论
    'comment_on_article': True, # 是否对这些用户的文章进行评论
    'comment_txt':'TTBot评论', # 对文章、视频、微头条进行评论的 共同评论内容
    'comment_article':'这是对文章的评论', # 对文章的评论，如果comment_txt参数已有，此项无效。需要comment_on_article为True
    'comment_count':1,          # 对各个类别（文章、视频、微头条）多少条数据进行评论
    'repost_on_article':False, # 是否对列表里的用户进行文章的转发
    'repost_txt':'TTBot转发',  # 转发头条媒体（文章、视频、微头条）时的评论内容
    'repost_count':1# 对各个类别（文章、视频、微头条）多少条数据进行转发并评论
    }
)
```

### <h3 id='2.9'>9. 定时器</h3>
 
 定时器可以根据给定的时间对特定的函数进行调用操作。具体模块为：`component.timer` 
 
 主要函数为`setup`、`run` 可见函数注释
 
 具体使用：
 * 使用`setup`函数进行定时器任务的注册
 * 所有定时任务注册完后调用`run`函数进行定时器运行
 
 示例代码：
 ```python
from component.toutiao import TTBot

bot = TTBot()
'''
定时任务 1：
1. 定时于 2019-07-20 15:10:00 执行 用户交互函数 interact_with_users
2. args 为 希望交互的用户uid列表，也是 interact_with_users 函数的位置参数
3. kwargs 为 interact_with_users 函数的关键字参数
'''
bot.timer.setup(
        '2019-07-20 15:10:00',
        bot.interact_with_users,
        args=(['75953693736','65445676041'],),
        kwargs={
                'comment_on_weitt':True,
                'comment_start_time':'2019-06-17 00:00:00',
                'comment_end_time':'2019-06-18 00:00:00',
                'comment_txt':'定时器评论',
                'comment_count':1,
                'repost_on_article':True,
                'repost_txt':'定时器转发',
                'repost_count':1
                },
    )

'''
定时任务 2：
1. 定时于 2019-07-25 15:10:00 使用登陆账户发布微头条  函数为 bot.account.post_weitt
2. args 为 bot.account.post_weitt 需要的位置参数，元组格式
3. looping 为 true 表示这个定时器任务会循环执行，间隔一段时间执行一次
4. frequency 为6 表示 这个定时器任务 1个小时内执行6次，也就是规定了间隔时间为:3600/6=600秒=10分钟
    即是10分钟执行一次
5.args_func 表示每一次任务执行时 函数bot.account.post_weitt 需要的位置参数 改变函数，即：
    第一次执行时 参数args为：('这是一个定时测试的微头条',) 执行完毕后 间隔10分钟
    第二次执行时 参数 args 为:
         args = lambda x:(f'{x[0]}-{time.time()}',) 的结果，其中x为第一次的参数，即：x=('这是一个定时测试的微头条',)
    所以 第二次执行的 args 为 ('这是一个定时测试的微头条-156663545.3658',)  
    依次类推，第三次执行时 参数args即为第二次执行时的args传入args_func后的结果
6.callbcak 函数为 执行完一次 定时函数bot.account.post_weitt 后的回调函数，其参数为 bot.account.post_weitt的返回结果
    即：
    此处callback=lambda x:print(x)，当定时任务执行后，x=bot.account.post_weitt('这是一个定时测试的微头条')
    即x为定时函数的返回结果传给callback回调
'''
bot.timer.setup(
        '2019-07-25 15:10:00',bot.account.post_weitt,
        args=('这是一个定时测试的微头条',),
        looping=True,
        frequency=6,
        args_func=lambda x:(f'{x[0]}-{time.time()}',),
        callback=lambda x:print(x))
    
# 注册完需要的定时任务1、2后 ，调用run运行定时器
bot.timer.run()
# 或者直接调用
bot.run_timer_jobs()
```
 

## 后续TODO
* 独立增加悟空问答 模块
* 增加 视频解析下载 模块
* 增加视频上传 模块

## 赞助支持

纯属个人维护，工作之余抽出时间进行维护（一般在周末和半夜）
> **Maybe you could buy me a cup of coffee :)**

alipay: ![aliapy](accessory/alipay.jpg)      wechat: ![wechat](accessory/wechat.png)

## 学习交流

- 微信公众号：刺派(微信号:pylinc)   
新开的公众号，分享关于python数据采集爬虫的技术经验,关注有惊喜
  
  ![公众号](accessory/qrcode.jpg)

- QQ 群: 刺派(qq群号:708736791)   
技术讨论交流 兼职接单

  ![QQ群](accessory/qq.png)
 
## 免责声明
* 本项目只作为娱乐学习使用，禁止使用本项目源码进行任何商业利用；
* 对使用本项目造成的一切风险及后果均由项目使用方负全责，请谨慎使用；

