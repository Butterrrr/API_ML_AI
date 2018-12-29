这里使用的是百度提供的图像识别中的车型识别API

请求代码示例：

<pre><code>
from aip import AipImageClassify

""" 你的 APPID AK SK """
APP_ID = '你的 App ID'
API_KEY = '你的 Api Key'
SECRET_KEY = '你的 Secret Key'

client = AipImageClassify(APP_ID, API_KEY, SECRET_KEY)

""" 读取图片 """
def get_file_content(filePath):
    with open(filePath, 'rb') as fp:
        return fp.read()

image = get_file_content('example.jpg')

""" 调用车辆识别 """
client.carDetect(image);

""" 如果有可选参数 """
options = {}
options["top_num"] = 3
options["baike_num"] = 5

""" 带参数调用车辆识别 """
client.carDetect(image, options)
</code></pre>



返回示例：
<pre><code>
{
  "log_id": 4086212218842203806,
  "location_result": {
    "width": 447,
    "top": 226,
    "height": 209,
    "left": 188
  },
  "result": [{
    "baike_info": {
      "baike_url": "http://baike.baidu.com/item/%E5%B8%83%E5%8A%A0%E8%BF%AAChiron/20419512",
      "description": "布加迪Chiron是法国跑车品牌布加迪出品的豪华超跑车。配置四涡轮增压发动机，420 公里每小时，有23种颜色的选择，售价高达260万美元。"
    },
    "score": 0.98793351650238,
    "name": "布加迪Chiron",
    "year": "无年份信息"
  },
  {
    "score": 0.0021970034576952,
    "name": "奥迪RS5",
    "year": "2011-2017"
  },
  {
    "score": 0.0021096928976476,
    "name": "奥迪RS4",
    "year": "无年份信息"
  },
  {
    "score": 0.0015581247862428,
    "name": "奥迪RS7",
    "year": "2014-2016"
  },
  {
    "score": 0.00082337751518935,
    "name": "布加迪威航",
    "year": "2004-2015"
  }],
  "color_result": "颜色无法识别"
}
</code></pre>
