### 说明

提供中国诗词相关接口，如诗词搜索，诗词详情，作者搜索，作者详情等。

如果现在所提供的接口不能满足你的要求，可以通过[http://blog.getlove.cn/article/5b289d7980ca8b10b8a173a3](http://blog.getlove.cn/article/5b289d7980ca8b10b8a173a3)联系我进行接口定制或者数据库的购买。

**公共请求参数及接口签名：[http://blog.getlove.cn/article/5c88d875641ec410596f3969](http://blog.getlove.cn/article/5c88d875641ec410596f3969)**

**服务器地址**

`https://account.getlove.cn/apiGetWay/5b010c7445657b2b64ada7a2` 

**示例代码（nodejs）**

[https://github.com/liuyinglong/api_get_way_demo/blob/master/example/poetry.js ](https://github.com/liuyinglong/api_get_way_demo/blob/master/example/poetry.js )

### 一、根据关键词搜索内容

#### 1、请求路径(请再路径前拼接服务器地址)

`/api/v1/poetry/search`

#### 2、请求参数

- query

| 参数     | 类型   | 必传 | 默认值 | 说明                                                         |
| -------- | ------ | ---- | ------ | ------------------------------------------------------------ |
| keywords | String | 是   |        | 搜索的关键词                                                 |
| type     | String | 否   |        | type当前支持的类型为`title`, `author` ,`text` 。不传入此参数则查询所有类型的数据(建议在第一页使用) |
| page     | Number | 否   | 1      | 页码，从第一页开始                                           |
| size     | Number | 否   | 1      | 每一页的查询的总次数（当前最大值为15，超过15则按照15来计算） |

#### 3、返回示例

- 请求：`/api/v1/poetry/search?keywords=此时此夜难为情&type=text`

  ```json
  {
      "code": 1000,
      "message": "success",
      "resp": {
          "page": 1,
          "data": [
              {
                  "_id": "59dcbea5ee1d825331ff34f6",
                  "title": "秋风清",
                  "author": {
                      "_id": "59dca987bddaf83748e8904c",
                      "dynastyText": "唐朝",
                      "name": "李白"
                  },
                  "straightMatter": "秋风清，秋月明。落叶聚还散，寒鸦栖复惊。相思相见知何日，此时此夜难为情。",
                  "tag": []
              }
          ],
          "count": 1
      }
  }
  ```

  

- 请求：`/api/v1/poetry/search?keywords=李白&size=1`

```json
{
    "code": 1000,
    "message": "success",
    "resp": {
        "titleList": {
            "page": 1,
            "data": [
                {
                    "_id": "59dcc9c4ee1d82533101b19f",
                    "title": "李白",
                    "author": {
                        "_id": "59dca9a2bddaf83748e89a44",
                        "dynastyText": "宋朝",
                        "name": "徐钧"
                    },
                    "straightMatter": "风骨神仙籍里人，诗狂酒圣且平生。开元一遇成何事，留得千秋万古名。",
                    "tag": []
                }
            ],
            "count": 1
        },
        "authorList": {
            "page": 1,
            "data": [
                {
                    "_id": "59dcbea3ee1d825331ff341a",
                    "title": "秋日鲁郡尧祠亭上宴别杜补阙范侍御",
                    "author": {
                        "_id": "59dca987bddaf83748e8904c",
                        "dynastyText": "唐朝",
                        "name": "李白"
                    },
                    "straightMatter": "我觉秋兴逸，谁云秋兴悲。山将落日去，水与晴空宜。鲁酒白玉壶，送行驻金羁。歇鞍憩古木，解带挂横枝。歌鼓川上亭，曲度神飙吹。云归碧海夕，雁没青天时。相失各万里，茫然空尔思。",
                    "tag": []
                }
            ],
            "count": 981
        },
        "textList": {
            "page": 1,
            "data": [
                {
                    "_id": "59dcbe82ee1d825331ff237c",
                    "title": "还人卷",
                    "author": {
                        "_id": "59dca987bddaf83748e8904d",
                        "dynastyText": "唐朝",
                        "name": "齐己"
                    },
                    "straightMatter": "李白李贺遗机杼，散在人间不知处。闻君收在芙蓉江，日斗鲛人织秋浦。金忆札札文离离。吴姬越女羞上机。鸳鸯浴烟鸾凤飞，澄江晓映馀霞辉。仙人手持玉刀尺，寸寸酬君珠与璧。裁作霞裳何处披，紫皇殿里深难觅。",
                    "tag": []
                }
            ],
            "count": 304
        }
    }
}
```

### 二、 获取诗词详情

#### 1、请求路径(请再路径前拼接服务器地址)

`/api/v1/poetry/detail/:poetryId`

#### 2、请求参数

- params

| 参数     | 类型   | 必传 | 默认值 | 说明     |
| -------- | ------ | ---- | ------ | -------- |
| poetryId | String | 是   | 无     | 诗词的ID |

#### 3、请求示例

- 请求 `/api/v1/poetry/detail/59dcbea4ee1d825331ff3432`

```json
{
    "code": 1000,
    "message": "success",
    "resp": {
        "_id": "59dcbea4ee1d825331ff3432",
        "title": "上之回",
        "author": {
            "_id": "59dca987bddaf83748e8904c",
            "dynastyText": "唐朝",
            "name": "李白",
            "resume": "\n                            李白（701年2月28日—762），字太白，号青莲居士。中国唐朝诗人，有“诗仙”之称，是伟大的浪漫主义诗人。汉族，祖籍陇西郡成纪县（今甘肃省平凉市静宁县南），出生于蜀郡绵州昌隆县（今四川省江油市青莲乡），一说生于西域碎叶（今吉尔吉斯斯坦托克马克）。逝世于安徽当涂县。其父李客，夫人有许氏、刘氏等四位，育二子（伯禽、天然）一女（平阳）。存世诗文千余篇，代表作有《蜀道难》、《行路难》、《梦游天姥吟留别》、《将进酒》等诗篇，有《李太白集》传世。公元762年病卒，享年61岁。其墓在安徽当涂，四川江油、湖北安陆有纪念馆。            "
        },
        "straightMatter": "三十六离宫，楼台与天通。阁道步行月，美人愁烟空。\n\n恩疏宠不及，桃李伤春风。淫乐意何极，金舆向回中。\n\n万乘出黄道，千旗扬彩虹。前军细柳北，后骑甘泉东。\n\n岂问渭川老，宁邀襄野童。秋暮瑶池宴，归来乐未穷。\n\n\n        ",
        "appreciation": "",
        "tag": [
            {
                "name": "忧国忧民",
                "_id": "59dd970953d50f16da6816cb"
            }
        ]
    }
}
```



### 三、获取作者详情

#### 1、请求路径(请再路径前拼接服务器地址)

`/api/v1/author/detail/:authorId`

#### 2、请求参数

- params

| 参数     | 类型   | 必传 | 默认值 | 说明     |
| -------- | ------ | ---- | ------ | -------- |
| authorId | String | 是   | 无     | 作者的ID |

#### 3、返回示例

- 请求 `/api/v1/author/detail/59dca987bddaf83748e8904c`

```json
{
    "code": 1000,
    "message": "success",
    "resp": {
        "_id": "59dca987bddaf83748e8904c",
        "dynastyText": "唐朝",
        "name": "李白",
        "resume": "\n                            李白（701年2月28日—762），字太白，号青莲居士。中国唐朝诗人，有“诗仙”之称，是伟大的浪漫主义诗人。汉族，祖籍陇西郡成纪县（今甘肃省平凉市静宁县南），出生于蜀郡绵州昌隆县（今四川省江油市青莲乡），一说生于西域碎叶（今吉尔吉斯斯坦托克马克）。逝世于安徽当涂县。其父李客，夫人有许氏、刘氏等四位，育二子（伯禽、天然）一女（平阳）。存世诗文千余篇，代表作有《蜀道难》、《行路难》、《梦游天姥吟留别》、《将进酒》等诗篇，有《李太白集》传世。公元762年病卒，享年61岁。其墓在安徽当涂，四川江油、湖北安陆有纪念馆。            "
    }
}
```



### 四、获取作者相关诗词

#### 1、请求路径(请再路径前拼接服务器地址)

`/api/v1/author/poetryList/:authorId`

#### 2、请求参数

- params

| 参数     | 类型   | 必传 | 默认值 | 说明     |
| -------- | ------ | ---- | ------ | -------- |
| authorId | String | 是   | 无     | 作者的ID |

- query

| 参数 | 类型   | 必传 | 默认值 | 说明                                                         |
| ---- | ------ | ---- | ------ | ------------------------------------------------------------ |
| page | Number | 否   | 1      | 页码，从第一页开始                                           |
| size | Number | 否   | 15     | 每一页的查询的总次数（当前最大值为15，超过15则按照15来计算） |



#### 3、返回示例

- 请求 `/api/v1/author/detail/59dca987bddaf83748e8904c?size=2`

```json
{
    "code": 1000,
    "message": "success",
    "resp": {
        "data": [
            {
                "_id": "59dcbea3ee1d825331ff341a",
                "title": "秋日鲁郡尧祠亭上宴别杜补阙范侍御",
                "author": {
                    "_id": "59dca987bddaf83748e8904c",
                    "dynastyText": "唐朝",
                    "name": "李白"
                },
                "straightMatter": "我觉秋兴逸，谁云秋兴悲。山将落日去，水与晴空宜。鲁酒白玉壶，送行驻金羁。歇鞍憩古木，解带挂横枝。歌鼓川上亭，曲度神飙吹。云归碧海夕，雁没青天时。相失各万里，茫然空尔思。",
                "tag": []
            },
            {
                "_id": "59dcbea3ee1d825331ff3421",
                "title": "冬夜醉宿龙门觉起言志",
                "author": {
                    "_id": "59dca987bddaf83748e8904c",
                    "dynastyText": "唐朝",
                    "name": "李白"
                },
                "straightMatter": "醉来脱宝剑，旅憩高堂眠。中夜忽惊觉，起立明灯前。开轩聊直望，晓雪河冰壮。哀哀歌苦寒，郁郁独惆怅。傅说版筑臣，李斯鹰犬人。欻起匡社稷，宁复长艰辛。而我胡为者，叹息龙门下。富贵未可期，殷忧向谁写。去去泪满襟，举声梁甫吟。青云当自致，何必求知音。",
                "tag": []
            }
        ],
        "count": 981,
        "pageNo": 1,
        "pageSize": 2
    }
}
```

