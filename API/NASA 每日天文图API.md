## NASA 每日天文图

### 说明

每日天文图数据由网站[https://apod.nasa.gov/apod/astropix.html](https://apod.nasa.gov/apod/astropix.html)提供。

此接口的数据由NASA开放api提供。我们获取到接口信息后，这些数据通过google翻译接口翻译成多种语言，并将其中图片或者视频传到国内的CDN，以提供更快的访问速度。

**公共请求参数及接口签名：[http://blog.getlove.cn/article/5c88d875641ec410596f3969](http://blog.getlove.cn/article/5c88d875641ec410596f3969)**

**服务器地址**（海外服务器，可能会出现速度较慢情况）

`https://account.getlove.cn/apiGetWay/5c889fded32e2a105ab0aaf3`

### 一、请求每月数据

#### 1、请求路径(请再路径前拼接服务器地址)

`/api/apod/language/:language/list/month/:month`

#### 2、请求参数

- params

| 参数     | 类型   | 说明                                                        |
| -------- | ------ | ----------------------------------------------------------- |
| language | String | 语言类型，目前支持 `zh-CN`,`zh-TW`,`fr`,`ja`,`ko`,`ru`,`en` |
| month    | String | 月份，格式为 `yyyy-mm`                                      |

#### 3、返回示例 

```json
{
  "code": 1000,
  "result": [
    {
      "language": {
        "zh-CN": {
          "title": "战车彗星",
          "explanation": "仍然在地球的夜空中翱翔，岩本彗星（C / 2018 Y1）与北方星座Auriga（Charioteer）的恒星和星云共享这个漂亮的望远镜视野。 2月27日，Iwamoto的绿色昏迷和微弱的尾巴出现在一个红色发射星云和开放星团M36（右下）之间。红色发射是来自氢气的光，这些氢气来自距离该地区大约6000光年远的巨大分子云附近的热星的紫外线辐射。来自彗星的绿色光芒，距离不到5分钟，主要是从太阳光中发出荧光的双原子碳分子发出的。 M36是Auriga最熟悉的星团之一，也是远远超出太阳系的背景物体，距离我们大约4000光年。 Iwamoto彗星于2月12日从地球最近的地方经过，并在一个高度椭圆形的轨道上向外运行，将它带到柯伊伯带之外。估计轨道周期为1，317年，应该在公元3390年返回内太阳系。"
        },
        "ja": {
          "title": "戦車の彗星",
          "explanation": "まだ地球の夜空を横切ってレースしている、岩本彗星（C / 2018 Y1）は、このかなり望遠鏡の視野を、北の星座Auriga、Charioteerの星雲と共有しています。 2月27日に捕獲された、岩本の緑がかったコマとかすかな尾は、赤みを帯びた放射星雲の複合体と開いている星団M36の間に現れます（右下）。赤みを帯びた発光は、この地域の巨大分子雲の近く、約6,000光年の距離にあるホットスターからの紫外線によってイオン化された水素ガスからの光です。彗星からの緑がかった輝きは、5光分以内で、主に日光の下で蛍光を発する二原子炭素分子からの放出です。 Aurigaのより身近な星団の1つであるM36も、太陽系をはるかに超えた、約4000光年後の背景のオブジェクトです。岩本彗星は2月12日に地球に最も接近して通過し、Kuiper帯を越えてそれを運ぶであろう高度に楕円形の軌道で外向きに束縛されている。 1,317年の推定軌道期間でそれは3390 ADの内側の太陽系に戻るべきです。"
        },
        "ru": {
          "title": "Комета Колесницы",
          "explanation": "Все еще летая по ночному небу планеты Земля, комета Ивамото (C / 2018 Y1) разделяет это красивое телескопическое поле зрения со звездами и туманностями северного созвездия Ауриги, Колесницы. Захваченные 27 февраля зеленоватая кома Ивамото и слабый хвост появляются между комплексом красноватых эмиссионных туманностей и открытым звездным скоплением M36 (справа внизу). Красноватое излучение - это свет от газообразного водорода, ионизированного ультрафиолетовым излучением горячих звезд вблизи гигантского молекулярного облака региона, расположенного на расстоянии около 6000 световых лет. Зеленоватое свечение от кометы, находящейся менее чем в 5 световых минутах, является преимущественно излучением молекул двухатомного углерода, флуоресцирующих на солнце. M36, одно из наиболее знакомых звездных скоплений Ауриги, также является фоновым объектом далеко за пределами Солнечной системы, на расстоянии около 4000 световых лет. Комета Ивамото прошла 12 февраля ближе всего к Земле и направлена наружу по высокоэллиптической орбите, которая унесет ее за пояс Койпера. С предполагаемым периодом обращения 1317 лет он должен вернуться во внутреннюю Солнечную систему в 3390 году нашей эры."
        }
      },
      "_id": "5c78e7b73263586f48eb9481",
      "date": "2019-03-01T00:00:00.000Z",
      "explanation": "Still racing across planet Earth's night skies, Comet Iwamoto (C/2018 Y1) shares this pretty telescopic field of view with stars and nebulae of northern constellation Auriga, the Charioteer. Captured on February 27, Iwamoto's greenish coma and faint tail appear between a complex of reddish emission nebulae and open star cluster M36 (bottom right). The reddish emission is light from hydrogen gas ionized by ultraviolet radiation from hot stars near the region's giant molecular cloud some 6,000 light-years distant. The greenish glow from the comet, less than 5 light-minutes away, is predominantly emission from diatomic carbon molecules fluorescing in sunlight. M36, one of Auriga's more familiar star clusters, is also a background object far beyond the Solar System, about 4,000 light-years away. Comet Iwamoto passed closest to Earth on February 12 and is outward bound in a highly elliptical orbit that will carry it beyond the Kuiper belt. With an estimated orbital period of 1,317 years it should return to the inner Solar System in 3390 AD.",
      "hdurl": "https://apod.nasa.gov/apod/image/1903/rolando-ligustri-C2018Y1_190227_FB_1551288721.jpg",
      "media_type": "image",
      "service_version": "v1",
      "title": "A Charioteer's Comet",
      "url": "https://apod.nasa.gov/apod/image/1903/rolando-ligustri-C2018Y1_190227_FB_1551288721_800.jpg",
      "copyright": "CARA Project",
      "__v": 0,
      "cdnUrl": "//hdPublic.getlove.cn/5c7a6d2949f9a50f19ef287c.jpg",
      "fileId": "5c7a6d2949f9a50f19ef287c"
    }
  ]
}
```



### 二、获取传入日期的数据

####  1、请求路径(请再路径前拼接服务器地址)

`/api/apod/language/:language/detail/date/:date`

#### 2、请求参数

- params

| 参数     | 类型   | 说明                                                        |
| -------- | ------ | ----------------------------------------------------------- |
| language | String | 语言类型，目前支持 `zh-CN`,`zh-TW`,`fr`,`ja`,`ko`,`ru`,`en` |
| date     | String | 日期，格式为 `yyyy-mm-dd`                                   |

#### 3、返回示例(中文简体 zh-CN)

```json
{
  "code": 1000,
  "result": {
    "language": {
      "zh-CN": {
        "title": "北春天空的亮点",
        "explanation": "你能在这个季节的夜空中看到什么？特色图形为地球北半球提供了一些亮点。作为一个以底部为中心的钟面，早期（北部）春季天空事件向左侧扇动，而晚春事件向右侧投射。一般来说，相对靠近地球的物体更接近于卡通人物，而望远镜位于底部中心 - 尽管几乎所有图像都可以在没有望远镜的情况下看到。正如在任何一个季节中所发生的那样，星座同年出现，并且像往常一样，Lyrids流星雨将在4月中旬达到顶峰。与往常一样，国际空间站（ISS）有时可以看作是日落后漂浮在天空中的亮点。在下周的春分之后，白天的长度将大于地球北半球的夜间长度，这种不平等将随着春季的发展而升级。随着春天的到来，木星在夜晚越来越明显。随着春天即将结束，五月将有两个满月，其中第二个称为蓝月亮。"
      }
    },
    "_id": "5c88b9ad1421636bc2a80a30",
    "date": "2019-03-13T00:00:00.000Z",
    "explanation": "What can you see in the night sky this season?  The featured graphic gives a few highlights for Earth's northern hemisphere. Viewed as a clock face centered at the bottom, early (northern) spring sky events fan out toward the left, while late spring events are projected toward the right. Objects relatively close to Earth are illustrated, in general, as nearer to the cartoon figure with the telescope at the bottom center -- although almost everything pictured can be seen without a telescope.  As happens during any season, constellations appear the same year to year, and, as usual, the Lyrids meteor shower will peak in mid-April.  Also as usual, the International Space Station (ISS) can be seen, at times, as a bright spot drifting across the sky after sunset.  After the Vernal Equinox next week, the length of daytime will be greater than the length of nighttime in Earth's northern hemisphere, an inequality that will escalate as the spring season develops.  Also as spring ages, Jupiter becomes visible increasingly earlier in the night. As spring draws to a close, the month of May will feature two full moons, the second of which is called a Blue Moon.",
    "hdurl": "https://apod.nasa.gov/apod/image/1903/SpringSky19_u2g_5000.jpg",
    "media_type": "image",
    "title": "Highlights of the North Spring Sky",
    "url": "https://apod.nasa.gov/apod/image/1903/SpringSky19_u2g_960.jpg",
    "cdnUrl": "//hdPublic.getlove.cn/5c88ba5a641ec410596f3967.jpg"
  }
}
```



### 三、获取最新日期的数据

#### 1、请求路径(请再路径前拼接服务器地址)

`/api/apod/language/:language/last`

#### 2、请求参数

- params

| 参数     | 类型   | 说明                                                        |
| -------- | ------ | ----------------------------------------------------------- |
| language | String | 语言类型，目前支持 `zh-CN`,`zh-TW`,`fr`,`ja`,`ko`,`ru`,`en` |

#### 3、返回示例（英文 en）

```json
{
  "code": 1000,
  "result": {
    "_id": "5c88b9ad1421636bc2a80a30",
    "date": "2019-03-13T00:00:00.000Z",
    "explanation": "What can you see in the night sky this season?  The featured graphic gives a few highlights for Earth's northern hemisphere. Viewed as a clock face centered at the bottom, early (northern) spring sky events fan out toward the left, while late spring events are projected toward the right. Objects relatively close to Earth are illustrated, in general, as nearer to the cartoon figure with the telescope at the bottom center -- although almost everything pictured can be seen without a telescope.  As happens during any season, constellations appear the same year to year, and, as usual, the Lyrids meteor shower will peak in mid-April.  Also as usual, the International Space Station (ISS) can be seen, at times, as a bright spot drifting across the sky after sunset.  After the Vernal Equinox next week, the length of daytime will be greater than the length of nighttime in Earth's northern hemisphere, an inequality that will escalate as the spring season develops.  Also as spring ages, Jupiter becomes visible increasingly earlier in the night. As spring draws to a close, the month of May will feature two full moons, the second of which is called a Blue Moon.",
    "hdurl": "https://apod.nasa.gov/apod/image/1903/SpringSky19_u2g_5000.jpg",
    "media_type": "image",
    "title": "Highlights of the North Spring Sky",
    "url": "https://apod.nasa.gov/apod/image/1903/SpringSky19_u2g_960.jpg",
    "cdnUrl": "//hdPublic.getlove.cn/5c88ba5a641ec410596f3967.jpg"
  }
}
```