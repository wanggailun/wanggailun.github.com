---
title: h5播放rtsp/rtmp
categories:
  - 记录
tags:
  - rtsp
  - h5  
date: 2021-09-22 17:40:00
---
借助VLC串流，使用h5video播放rtsp/rtmp流
<!--more-->
p>h5 video标签不支持直接播放rtsp流数据，故需要借助VLC转码处理后使用video标签播放  </p>
<ol>
<li><a target="_blank" rel="noopener" href="https://www.videolan.org/vlc/">下载VLC软件</a></li>
<li>安装后打开 媒体-&gt;打开网络串流<br><img src="/images/rtsp/rtsp1.png" alt="b.wguan.top"></li>
<li>输完地址之后在右下角选择串流<br>例如： rtmp://58.200.131.2:1935/livetv/cctv1<br><img src="/images/rtsp/rtsp2.png" alt="b.wguan.top"><br><img src="/images/rtsp/rtsp3.png" alt="b.wguan.top"></li>
<li>点击底下的下一步-&gt;Http,选中HTTP<br> <img src="/images/rtsp/rtsp4.png" alt="b.wguan.top"></li>
<li>然后点击右边的添加-&gt;在路径处写上/cctv1,转换出来的视频流地址为如<a target="_blank" rel="noopener" href="http://localhost:8080/cctv1">http://localhost:8080/cctv1</a><br> <img src="/images/rtsp/rtsp5.png" alt="b.wguan.top"></li>
<li>h5播放<br> <code>&lt;video src=&quot;http://localhost:8080/cctv1&quot; autoplay controls style=&quot;width: 500px;height: 500px;&quot;&gt;&lt;/video&gt;</code></li>
<li>各摄像头rtsp组成<br>a：英飞拓<br>rtsp://ip:port/1/h264major<br>rtsp://192.168.2.100:554/1/h264major<br>b：大华<br>rtsp://username:password@ip:port/cam/realmonitor?channel=1&amp;subtype=0<br>rtsp://admin123:<a href="mailto:admin123@172.16.0.155">admin123@172.16.0.155</a>:554/cam/realmonitor?channel=1&amp;subtype=1<br>c：海康<br>rtsp://[username]:[password]@[ip]:[port]/[codec]/[channel]/[subtype]/av_stream<br>rtsp://admin:<a href="mailto:hik12345@192.168.8.125">hik12345@192.168.8.125</a>:554/h264/ch33/main/av_stream<br>rtsp://admin:<a href="mailto:hik12345@192.168.8.125">hik12345@192.168.8.125</a>:554/h264/ch33/sub/av_stream<br>rtsp://admin:<a href="mailto:hik12345@192.168.8.125">hik12345@192.168.8.125</a>:554/h264/ch34/main/av_stream  </li>
<li>在线rtmp资源</li>
</ol>
<ul>
<li>CCTV-1综合:rtmp://58.200.131.2:1935/livetv/cctv1  </li>
<li>CCTV-2财经:rtmp://58.200.131.2:1935/livetv/cctv2</li>
<li>CCTV-3综艺:rtmp://58.200.131.2:1935/livetv/cctv3</li>
<li>CCTV-4中文国际:rtmp://58.200.131.2:1935/livetv/cctv4</li>
<li>CCTV-5体育:rtmp://58.200.131.2:1935/livetv/cctv5</li>
<li>CCTV-6电影:rtmp://58.200.131.2:1935/livetv/cctv6</li>
<li>CCTV-7军事农业:rtmp://58.200.131.2:1935/livetv/cctv7</li>
<li>CCTV-8电视剧:rtmp://58.200.131.2:1935/livetv/cctv8</li>
<li>CCTV-9记录:rtmp://58.200.131.2:1935/livetv/cctv9</li>
<li>CCTV-10科教:rtmp://58.200.131.2:1935/livetv/cctv10</li>
<li>CCTV-11戏曲:rtmp://58.200.131.2:1935/livetv/cctv11</li>
<li>CCTV-12社会与法:rtmp://58.200.131.2:1935/livetv/cctv12</li>
<li>CCTV-13新闻:rtmp://58.200.131.2:1935/livetv/cctv13</li>
<li>CCTV-14少儿:rtmp://58.200.131.2:1935/livetv/cctv14</li>
<li>CCTV-15音乐:rtmp://58.200.131.2:1935/livetv/cctv15</li>
<li>安徽卫视:rtmp://58.200.131.2:1935/livetv/ahtv</li>
<li>兵团卫视:rtmp://58.200.131.2:1935/livetv/bttv</li>
<li>重庆卫视:rtmp://58.200.131.2:1935/livetv/cqtv</li>
<li>东方卫视:rtmp://58.200.131.2:1935/livetv/dftv</li>
<li>东南卫视:rtmp://58.200.131.2:1935/livetv/dntv</li>
<li>广东卫视:rtmp://58.200.131.2:1935/livetv/gdtv</li>
<li>广西卫视:rtmp://58.200.131.2:1935/livetv/gxtv</li>
<li>甘肃卫视:rtmp://58.200.131.2:1935/livetv/gstv</li>
<li>贵州卫视:rtmp://58.200.131.2:1935/livetv/gztv</li>
<li>湖北卫视:rtmp://58.200.131.2:1935/livetv/hbtv</li>
<li>湖南卫视:rtmp://58.200.131.2:1935/livetv/hunantv</li>
<li>河北卫视:rtmp://58.200.131.2:1935/livetv/hebtv</li>
<li>河南卫视:rtmp://58.200.131.2:1935/livetv/hntv</li>
<li>黑龙江卫视:rtmp://58.200.131.2:1935/livetv/hljtv</li>
<li>江苏卫视:rtmp://58.200.131.2:1935/livetv/jstv</li>
<li>江西卫视:rtmp://58.200.131.2:1935/livetv/jxtv</li>
<li>吉林卫视:rtmp://58.200.131.2:1935/livetv/jltv</li>
<li>辽宁卫视:rtmp://58.200.131.2:1935/livetv/lntv</li>
<li>内蒙古卫视:rtmp://58.200.131.2:1935/livetv/nmtv</li>
<li>宁夏卫视:rtmp://58.200.131.2:1935/livetv/nxtv</li>
<li>青海卫视:rtmp://58.200.131.2:1935/livetv/qhtv</li>
<li>四川卫视:rtmp://58.200.131.2:1935/livetv/sctv</li>
<li>山东卫视:rtmp://58.200.131.2:1935/livetv/sdtv</li>
<li>山西卫视:rtmp://58.200.131.2:1935/livetv/sxrtv</li>
<li>陕西卫视:rtmp://58.200.131.2:1935/livetv/sxtv</li>
<li>山东教育:rtmp://58.200.131.2:1935/livetv/sdetv</li>
<li>中国教育-1:rtmp://58.200.131.2:1935/livetv/cetv1</li>
<li>中国教育-3:rtmp://58.200.131.2:1935/livetv/cetv3</li>
<li>中国教育-4:rtmp://58.200.131.2:1935/livetv/cetv4</li>
<li>CCTV-第一剧场:rtmp://58.200.131.2:1935/livetv/dyjctv</li>
<li>CCTV-国防军事:rtmp://58.200.131.2:1935/livetv/gfjstv</li>
<li>CCTV-怀旧剧场:rtmp://58.200.131.2:1935/livetv/hjjctv</li>
<li>CCTV-风云剧场:rtmp://58.200.131.2:1935/livetv/fyjctv</li>
<li>CCTV-风云足球:rtmp://58.200.131.2:1935/livetv/fyzqtv</li>
<li>CCTV-风云音乐:rtmp://58.200.131.2:1935/livetv/fyyytv</li>
<li>CCTV-世界地理:rtmp://58.200.131.2:1935/livetv/sjdltv</li>
<li>CCTV-1HD:rtmp://58.200.131.2:1935/livetv/cctv1hd</li>
<li>CCTV-2HD:rtmp://58.200.131.2:1935/livetv/cctv2hd</li>
<li>CCTV-3HD:rtmp://58.200.131.2:1935/livetv/cctv3hd</li>
<li>CCTV-4HD:rtmp://58.200.131.2:1935/livetv/cctv4hd</li>
<li>CCTV-5HD:rtmp://58.200.131.2:1935/livetv/cctv5hd</li>
<li>CCTV5+HD:rtmp://58.200.131.2:1935/livetv/cctv5phd</li>
<li>CCTV-6HD:rtmp://58.200.131.2:1935/livetv/cctv6hd</li>
<li>CCTV-7HD:rtmp://58.200.131.2:1935/livetv/cctv7hd</li>
<li>CCTV-8HD:rtmp://58.200.131.2:1935/livetv/cctv8hd</li>
<li>CCTV-9HD:rtmp://58.200.131.2:1935/livetv/cctv9hd</li>
<li>CCTV-10HD:rtmp://58.200.131.2:1935/livetv/cctv10hd</li>
<li>CCTV-12HD:rtmp://58.200.131.2:1935/livetv/cctv12hd</li>
<li>CCTV-14HD:rtmp://58.200.131.2:1935/livetv/cctv14hd</li>
<li>CGTN-新闻:rtmp://58.200.131.2:1935/livetv/cctv16</li>
<li>CETV-1:rtmp://58.200.131.2:1935/livetv/cetv1</li>
<li>CETV-3:rtmp://58.200.131.2:1935/livetv/cetv3</li>
<li>CETV-4:rtmp://58.200.131.2:1935/livetv/cetv4</li>
<li>北京卫视高清:rtmp://58.200.131.2:1935/livetv/btv1hd</li>
<li>北京影视高清:rtmp://58.200.131.2:1935/livetv/btv4hd</li>
<li>北京体育高清:rtmp://58.200.131.2:1935/livetv/btv6hd</li>
<li>北京新闻高清:rtmp://58.200.131.2:1935/livetv/btv9hd</li>
<li>北京纪实高清:rtmp://58.200.131.2:1935/livetv/btv11hd</li>
<li>北京卫视:rtmp://58.200.131.2:1935/livetv/btv1</li>
<li>北京文艺:rtmp://58.200.131.2:1935/livetv/btv2</li>
<li>北京科教:rtmp://58.200.131.2:1935/livetv/btv3</li>
<li>北京影视:rtmp://58.200.131.2:1935/livetv/btv4</li>
<li>北京财经:rtmp://58.200.131.2:1935/livetv/btv5</li>
<li>北京体育:rtmp://58.200.131.2:1935/livetv/btv6</li>
<li>北京生活:rtmp://58.200.131.2:1935/livetv/btv7</li>
<li>北京青年:rtmp://58.200.131.2:1935/livetv/btv8</li>
<li>北京新闻:rtmp://58.200.131.2:1935/livetv/btv9</li>
<li>北京卡酷:rtmp://58.200.131.2:1935/livetv/btv10</li>
<li>北京文艺高清:rtmp://58.200.131.2:1935/livetv/btv2hd</li>
<li>安徽卫视高清:rtmp://58.200.131.2:1935/livetv/ahhd</li>
<li>重庆卫视高清:rtmp://58.200.131.2:1935/livetv/cqhd</li>
<li>东方卫视高清:rtmp://58.200.131.2:1935/livetv/dfhd</li>
<li>天津卫视高清:rtmp://58.200.131.2:1935/livetv/tjhd</li>
<li>东南卫视高清:rtmp://58.200.131.2:1935/livetv/dnhd</li>
<li>江西卫视高清:rtmp://58.200.131.2:1935/livetv/jxhd</li>
<li>河北卫视高清:rtmp://58.200.131.2:1935/livetv/hebhd</li>
<li>湖南卫视高清:rtmp://58.200.131.2:1935/livetv/hunanhd</li>
<li>湖北卫视高清:rtmp://58.200.131.2:1935/livetv/hbhd</li>
<li>辽宁卫视高清:rtmp://58.200.131.2:1935/livetv/lnhd</li>
<li>四川卫视高清:rtmp://58.200.131.2:1935/livetv/schd</li>
<li>江苏卫视高清:rtmp://58.200.131.2:1935/livetv/jshd</li>
<li>浙江卫视高清:rtmp://58.200.131.2:1935/livetv/zjhd</li>
<li>山东卫视高清:rtmp://58.200.131.2:1935/livetv/sdhd</li>
<li>广东卫视高清:rtmp://58.200.131.2:1935/livetv/gdhd</li>
<li>深圳卫视高清:rtmp://58.200.131.2:1935/livetv/szhd</li>
<li>黑龙江卫视高清:rtmp://58.200.131.2:1935/livetv/hljhd</li>
<li>CHC高清电影:rtmp://58.200.131.2:1935/livetv/chchd</li>
<li>上海纪实高清:rtmp://58.200.131.2:1935/livetv/docuchina</li>
<li>金鹰纪实高清:rtmp://58.200.131.2:1935/livetv/gedocu</li>
<li>全纪实高清:rtmp://58.200.131.2:1935/livetv/documentaryhd</li>
<li>凤凰卫视中文台:rtmp://58.200.131.2:1935/livetv/fhzw</li>
<li>凤凰卫视资讯台:rtmp://58.200.131.2:1935/livetv/fhzx</li>
<li>凤凰卫视电影台:rtmp://58.200.131.2:1935/livetv/fhdy</li>
<li>星空卫视:rtmp://58.200.131.2:1935/livetv/startv</li>
<li>Star Sports:rtmp://58.200.131.2:1935/livetv/starsports</li>
<li>Channel[V]:rtmp://58.200.131.2:1935/livetv/channelv</li>
<li>探索频道:rtmp://58.200.131.2:1935/livetv/discovery</li>
<li>国家地理频道:rtmp://58.200.131.2:1935/livetv/natlgeo</li>
<li>CHC家庭影院:rtmp://58.200.131.2:1935/livetv/chctv</li>
<li>CHC动作电影:rtmp://58.200.131.2:1935/livetv/chcatv</li>
<li>美国电视频道:rtmp://media3.scctv.net/live/scctv_800</li>
<li>香港财经:rtmp://202.69.69.180:443/webcast/bshdlive-pc</li>
</ul>
