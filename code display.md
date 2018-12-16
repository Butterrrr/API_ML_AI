这里使用的是百度提供的图像识别中的车型识别API

请求代码示例：

<pre><code>
# encoding:utf-8
import base64
import urllib
import urllib2

'''
车型识别
'''

request_url = "https://aip.baidubce.com/rest/2.0/image-classify/v1/car"

# 二进制方式打开图片文件
f = open('[本地文件]', 'rb')
img = base64.b64encode(f.read())

params = {"image":img,"top_num":5}
params = urllib.urlencode(params)

access_token = '[调用鉴权接口获取的token]'
request_url = request_url + "?access_token=" + access_token
request = urllib2.Request(url=request_url, data=params)
request.add_header('Content-Type', 'application/x-www-form-urlencoded')
response = urllib2.urlopen(request)
content = response.read()
if content:
    print content
</code></pre>


返回示例：

<pre><code>
HTTP/1.1 200 OK
x-bce-request-id: 73c4e74c-3101-4a00-bf44-fe246959c05e
Cache-Control: no-cache
Server: BWS
Date: Tue, 18 Oct 2016 02:21:01 GMT
Content-Type: application/json;charset=UTF-8
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