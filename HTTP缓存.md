缓存一般由服务器控制(通过某些方式可以本地控制缓存，比如向过滤器添加缓存控制信息)。通过在请求头添加下面几个字端：

Request:  
<table>
<tr> <td>请求头字段</td><td>意义</td> </tr>
<tr> <td>If-Modified-Since:Sun, 03 Jan 2016 03:47:16 GMT</td><td>缓存文件的最后修改时间</td> </tr>
<tr> <td>If-None-Match:“3415g77s19tc3:0″</td><td>缓存文件的Etag(Hash)值</td> </tr>
<tr> <td>Cache-Control:no-cache</td><td>	不使用缓存</td> </tr>
<tr> <td>Pragma:no-cache</td><td>不使用缓存</td> </tr>
</table>

Response:
<table>
<tr> <td>响应头字段</td><td>意义</td> </tr>
<tr> <td>Cache-Control: public</td><td>响应被共有缓存，移动端无用</td> </tr>
<tr> <td>Cache-Control: private</td><td>	响应被私有缓存，移动端无用</td> </tr>
<tr> <td>Cache-Control:no-cache</td><td>不缓存</td> </tr>
<tr> <td>Cache-Control:no-store</td><td>不缓存</td> </tr>
<tr> <td>Cache-Control: max-age=60</td><td>60秒之后缓存过期（相对时间）</td> </tr>
<tr> <td>Date: Sun, 03 Jan 2016 04:07:01 GMT</td><td>当前response发送的时间</td> </tr>
<tr> <td>Expires: Sun, 03 Jan 2016 07:07:01 GMT</td><td>缓存过期的时间（绝对时间）</td> </tr>
<tr> <td>Last-Modified: Sun, 03 Jan 2016 04:07:01 GMT</td><td>服务器端文件的最后修改时间</td> </tr>
<tr> <td>ETag: “3415g77s19tc3:0″</td><td>服务器端文件的Etag[Hash]值</td> </tr>
</table>

正式使用时按需求也许只包含其中部分字段。
客户端要根据这些信息储存这次请求信息。
然后在客户端发起请求的时候要检查缓存。遵循下面步骤：  

![](http://mmbiz.qpic.cn/mmbiz/FoiciaVBBCfia79CBfLBBKMbfwrwSMXHU9GuqVXcMS4mY03MIApZOXCJdhutPBctnB36TSsb4dyVkfcLN51tF7wsw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1)
  
[Android网络请求心路历程（上）](http://mp.weixin.qq.com/s?__biz=MzA3MDMyMjkzNg==&amp;mid=402574975&amp;idx=1&amp;sn=2e7a23363957cafcf4e442b19d3a3e90&amp;scene=1&amp;srcid=0111YoZiN3LmXy7jrnfqlCUm#rd)  
[Android网络请求心路历程（下）](http://mp.weixin.qq.com/s?__biz=MzA3MDMyMjkzNg==&amp;mid=402574975&amp;idx=2&amp;sn=61f671ec09fccbe06fe2709d97839bab&amp;scene=1&amp;srcid=01115jXWCWIuOVasjMlt1ilI#rd)  

[Web缓存机制系列](http://www.alloyteam.com/2012/03/web-cache-1-web-cache-overview/)[AlloyTeam]  
[HTTP缓存](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching?hl=zh-cn)[Google Web]  
[HTTP 缓存策略](http://foofish.net/blog/95/http-cache-policy)