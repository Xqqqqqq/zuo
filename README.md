# zuodesign-vue

*设置接口内容不为空：thisdata != null
*原因：加载数据会比引入数据快，所以判断是否引入数据，如果未引入数据，不进行加载
*定义一个变量，用来接受数组：thisdata
*使用thisdata接收数据的数组：that.thisdata=res.data;
*鼠标移入变放大镜：cursor: zoom-in
*给页面加滚动条:overflow-y: auto; overflow-x: hidden;
