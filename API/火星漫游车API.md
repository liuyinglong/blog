### 说明

此API旨在收集NASA在火星上的好奇号，机遇号和勇气号探测器收集的图像数据，并使其更容易被其他开发人员，教育工作者和科学家使用。为提升图像的访问速度，部分图像将提供七牛全球CDN。

**公共请求参数及接口签名：[http://blog.getlove.cn/article/5c88d875641ec410596f3969](http://blog.getlove.cn/article/5c88d875641ec410596f3969)**

**服务器地址**（海外服务器，可能会出现速度较慢的情况）:

`https://account.getlove.cn/apiGetWay/5c889fded32e2a105ab0aaf3`

**示例代码（nodejs）**

[https://github.com/liuyinglong/api_get_way_demo/blob/master/example/mars_over.js ](https://github.com/liuyinglong/api_get_way_demo/blob/master/example/mars_over.js )

### 一、获取漫游车拍摄的图片

#### 1、请求路径(请再路径前拼接服务器地址)

`/api/mars/rover/:rover`

#### 2、请求参数

- params

| 参数  | 类型   | 默认值 | 说明                                                         |
| ----- | ------ | ------ | ------------------------------------------------------------ |
| rover | String | 无     | 火星车的名字 `curiosity`, `opportunity`, `spirit`,分别为好奇号，机遇号，勇气号 |

- query

| 参数      | 类型   | 默认值                   | 说明                                 |
| --------- | ------ | ------------------------ | ------------------------------------ |
| earthDate | String | 传入的火星车的最新的日期 | 地球上的日期                         |
| camera    | String | 无                       | 不传入此参数，则获取所有摄像头的数据 |

- `camera`摄像头说明

| Abbreviation | Camera                                             | Curiosity | Opportunity | Spirit |
| ------------ | -------------------------------------------------- | --------- | ----------- | ------ |
| FHAZ         | Front Hazard Avoidance Camera                      | ✔         | ✔           | ✔      |
| RHAZ         | Rear Hazard Avoidance Camera                       | ✔         | ✔           | ✔      |
| MAST         | Mast Camera                                        | ✔         |             |        |
| CHEMCAM      | Chemistry and Camera Complex                       | ✔         |             |        |
| MAHLI        | Mars Hand Lens Imager                              | ✔         |             |        |
| MARDI        | Mars Descent Imager                                | ✔         |             |        |
| NAVCAM       | Navigation Camera                                  | ✔         | ✔           | ✔      |
| PANCAM       | Panoramic Camera                                   |           | ✔           | ✔      |
| MINITES      | Miniature Thermal Emission Spectrometer (Mini-TES) |           | ✔           | ✔      |

#### 3、返回示例

| 参数        | 描述                                          | 示例       |
| ----------- | --------------------------------------------- | ---------- |
| endDate     | 目前最新的日期（机遇号/勇气号的数据不会更新） | 2019-03-06 |
| startDate   | 开始日期                                      | 2019-03-06 |
| currentDate | 数据的日期                                    | 2012-08-06 |
| photos      | 图片列表                                      |            |



```json
{
  "code": 0,
  "data": {
    "photos": [
      {
        "camera": {
          "id": 23,
          "name": "CHEMCAM",
          "rover_id": 5,
          "full_name": "Chemistry and Camera Complex"
        },
        "_id": "5c82ada16e64d116baa3ebd6",
        "id": "671393",
        "sol": 2339,
        "img_src": "http://mars.jpl.nasa.gov/msl-raw-images/proj/msl/redops/ods/surface/sol/02339/opgs/edr/ccam/CR0_605136491EDR_F0740762CCAM02339M_.JPG",
        "earth_date": "2019-03-06T00:00:00.000Z",
        "rover": "curiosity"
      }
    ],
    "endDate": "2019-03-06",
    "startDate": "2012-08-06",
    "currentDate": "2019-03-06"
  }
}
```

