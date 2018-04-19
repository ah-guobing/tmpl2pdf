# tmpl2pdf
根据PDF模板动态生成PDF文件<br />
使用场景：各类电子协议、电子证书、电子发票的制作<br />
要求自行使用 Adobe Acrobat 制作PDF表单模板，网上资料很多，请自己查阅。


## 服务端
### 环境要求
JDK：jdk1.8

### 服务启动
&#35; nohup java -jar serv.jar --server.port=端口号 --pdftmpl.dir.src=PDF模板目录 --pdfout.dir.dest=PDF输出目录 >>./serv.log &<br />
如：<br />&#35; nohup java -jar serv.jar --server.port=8091 --pdftmpl.dir.src=/root/tmpl2pdf/tmpl/ --pdfout.dir.dest=/root/tmpl2pdf/out/ >>./serv.log &

&#35;&#35; 检测微服务是否正常<br />
&#35; netstat -anp | grep 上一步指定的端口号



## 客户端调用
任何客户端可通过HTTP请求来调用服务
### 版本查看
<table>
  <tr>
    <th colspan="2" align="left">GET http://192.168.1.88:8091/info</th>
  </tr>
  <tr>
    <th>参数</th>
    <th>说明</th>
  </tr>
  <tr>
    <td>无</td>
    <td>无</td>
  </tr>
</table>

### 根据PDF模板动态生成PDF文件
<table>
  <tr>
    <th colspan="3" align="left">POST http://192.168.1.88:8091/create</th>
  </tr>
  <tr>
    <th>参数</th>
    <th>是否必须</th>
    <th>说明</th>
  </tr>
  <tr>
    <td>tmpl</td>
    <td>*</td>
    <td>PDF模板文件名（不含后缀，如tmplfile1）</td>
  </tr>
  <tr>
    <td>out</td>
    <td>*</td>
    <td>生成的PDF文件名（不含后缀，如pdffile1）</td>
  </tr>
  <tr>
    <td>data</td>
    <td>*</td>
    <td>PDF模板中的表单域及对应的值，以json格式传递，如：<br/>{
	"name": "张三丰2222",
	"addr": "中国上海市"
}</td>
  </tr>
	  <tr>
    <td>fontSize</td>
    <td></td>
    <td>定义PDF文字字号，如：8，默认值为8</td>
  </tr>
  <tr>
    <td>lastModifiedTime</td>
    <td></td>
    <td>若指定，则将生成的PDF文件的最后修改时间置为指定值，如：<br />2008-12-12 12:00:00</td>
  </tr>
</table>


## 问题反馈
使用中若有问题请联系QQ：46926125
