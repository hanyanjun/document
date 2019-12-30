# 项目列表
- [项目库web端](#news)
- [项目库小程序](#mini)
- [知识图谱browser](#kg)
- [交易系统](#trade)
- [otcCharts](#chart)
- [官网](#web)

<h2 id="news">项目库web端</h2>

- 1.源码地址：
[点击跳转](https://github.com/xorder-project/newsWeb)
- 2.项目框架
```
项目使用主要框架及插件：react，antd，axios，react-router-dom，redux，react-redux，sass，md5 , redux-thunk ， semantic等；
```
- 3.命令
```
启动本地服务: npm run dev 或者 npm run start 

文件打包: npm run build

自定义webpack配置： npm run eject(不可逆)
```
- 4.开发注意
  - 4.1 权限控制
  > 该项目的权限控制的拦截通过:src/components/AuthRouter/  + redux 去实现控制
  - 4.2 接口封装
  > 接口封装目录：newsWeb/src/fetch/；

  > 在axios的基础上加上请求，响应拦截功能；

  > 在拦截基础上添加loading的显示的配置；

  > 在axios的基础上添加promise的回调方便调用.then .catch ；

  > 对axios的get 和 post 封装为 gAJAX 和 pAJAX , 需要其他方式自行封装；
  
  > 连接其他电脑的服务器后端通过package.json 中的 proxy 配置；

  > 异步操作通过redux-thunk；
  - 4.3 UI框架
  > 除了使用antd 之外 由于里面包含了部分h5相关的代码 又加入 antd-mobil ， web端使用的是antd + semantic ；
- 5.其他
   > 暂无
<h2 id="mini">项目库小程序</h2>

- 1.源码地址：
[点击跳转](https://github.com/xorder-project/Mini-Programs)
- 2.项目框架
```
项目使用主要框架及插件：flyio ， mpvue ， js-md5 ， moment ，vuex，color-ui 等；
```
- 3.命令
```
启动本地服务: npm run start 

文件打包: npm run build
```
- 4.开发注意
  - 4.1 权限控制
  > 该项目的权限控制的拦截通过:/src/fetch/api.js 中的 响应拦截，根据code值来进行重定向；
  - 4.2 接口封装
  > 接口封装目录：/src/fetch/api.js ；

  > 在flyio的基础上加上请求，响应拦截功能；

  > 在拦截基础上添加loading的显示的配置；

  > 在axios的基础上添加promise的回调方便调用.then .catch ；
  
  > 连接其他电脑的服务器后端通过设置：fly.config.baseURL；

  - 4.3 UI框架
  > 使用color-ui
- 5.其他
   - 5.1 特殊方法调用
   ```
   在vue.prototype 分别添加：
   $api = fly;
   $utils;
   $Toast;
   $Message 对象 ， 可以通过例如： this.$api 的形式进行调用；
   ```
   - 5.2 关于vuex
   > vuex 中的功能 只能使用commit方法去改变store中state;
   - 5.3 关于小程序组件
   > 组件需要在json文件中进行注册，然后到对用vue文件中才可以使用；
   - 5.4 关于页面缓存
   > 参照mpvue文档以及小程序文档；

<h2 id="kg">知识图谱browser</h2>

- 1.源码地址：
[点击跳转](https://github.com/xorder-project/neo4j-browser/tree/master/d3-brower)

- 2.项目框架
```
项目使用主要框架及插件：react，antd，axios，react-router-dom，redux，react-redux，neo4j-data，react-zmage，styled-components，jquery，d3，sass，md5 , redux-thunk 等
```
- 3.命令
```
启动服务: npm run start 

文件打包: npm run build

自定义webpack配置： npm run eject(不可逆)

```
- 4.开发注意
  - 4.1 权限控制
  > 该项目的权限控制的拦截通过:/src/fetch/api.js 中的 响应拦截，根据code值来进行重定向；
  - 4.2 接口封装
  > 接口封装目录：/src/fetch/api.js ；

  > 在axios的基础上加上请求，响应拦截功能；

  > 在拦截基础上添加loading的显示的配置；

  > 在axios的基础上添加promise的回调方便调用.then .catch ；
  
  > 连接其他电脑的服务器后端通过设置：fly.config.baseURL；

  - 4.3 UI框架
  > antd
- 5.关于neo4j-data

  - 5.1 npm包地址
  [点击跳转](https://www.npmjs.com/package/neo4j-data)

  - 5.2 此包说明
  > 此包是用于通过match语句来匹配数据库中的节点和关系，并且将获取到数据进行序列化；

  - 5.3 引入方式
  ```
  支持 ES module

  import neo4jData from "neo4j-data"

  支持CJS

  var neo4jData = require("neo4jData");
  支持AMD

  require(['neo4j-data'],function(neo4j-data){
   ...
   ...
   ...
  })
  支持link

  <script src="https://unpkg.com/neo4j-data"></script>
  ```  
  - 5.4 使用实例
  ```
    import neo4jData from "neo4j-data"


    const neo4j = new neo4jData();
    <!-- 初始化配置 -->
    neo4j.config({
        url : '填入url',
        username : '填入用户名',
        password : '填入密码'
    })
    <!-- 运行match语句 -->
    neo4j.runMatch(
        "需要执行的MATCH语句"
        )
        .then(result=>{
            <!-- 对结果进行处理  -->
            let info = neo4j.dataDetail(result.records);
            neo4j.close();
    })
  ```
  - 5.5 处理后数据
  ```
  {
        
    nodes: [{…}, {…}, {…}, {…}, {…}, {…}, {…}],
    nodesMap: {239979: {…}, 263732: {…}, 441610: {…}, 458585: {…}, 459032: {…}, 481273: {…}, 482247: {…}},
    relationships: [{…}, {…}, {…}, {…}, {…}, {…}, {…}],
    relationshipsMap:  {239979: {…}, 263732: {…}, 441610: {…}, 458585: {…}, 459032: {…}, 481273: {…}, 482247: {…}},
  }
  ```

  - 5.6 注意
  > 如果通过match语句获取到的数据没有连线，那么请勿使用neo4j.dataDetail方法去处理数据，因为处理只有会将原有的获取到的独立的节点给过滤掉；
- 6. 关于 react-d3-force

  - 6.1 npm包地址
  [点击跳转](https://www.npmjs.com/package/react-d3-force)

  - 6.2 此包说明

  >此包是知识图谱的可视化包，主要用于通过match语句获取到的序列化的节点关系进行可视化的展示；

  - 6.3 graph方法列表

  > 对应的方法，代码中都有体现，可以对照代码调用下面的方法
  ```

  exportPNG 

  gainPngBase64

  graphInit 

  retainNodesRel

  addNodesRel

  extendNodesRel

  gainRelByNode

  resetGraph

  clearSelected

  toggleByLabels

  removeByLabels

  updateNodesRel

  updateOneNode

  removeNode

  updateStyleNodesRel

  zoomOut

  zoomIn

  initGraph

  ```
  - 6.4 事件方法列表：
  
  > 对应的方法，代码中都有体现，可以对照代码调用下面的方法；

  ```

  nodeMouseOver

  nodeMouseOut

  menuMouseOver

  menuMouseOut

  relMouseOver

  relMouseOut

  relationshipClicked

  canvasClicked

  nodeClose

  nodeClicked

  nodeDblClicked

  nodeUnlock

  nodeDelete

  nodeNew

  nodeEdit

  nodeCtrlClick

  nodeClickRight

  contrarySelected

  clearSelected

  backStatus

  initStatus

  startFrame

  madeChart

  addRel
  ```
<h2 id="trade">交易系统</h2>


- 1.源码地址：
[点击跳转](https://github.com/xorder-project/tradingSystemWeb)

- 2.项目框架
```
项目使用主要框架及插件：vue，vuex，vue-router，antd，ccxt，js-md5，stompjs，echarts，tradingview，vueScroll 等；
```

- 3.命令
```
启动本地服务: npm run dev 或者 npm run start 

文件打包: npm run build

```
- 4.开发注意
  - 4.1 权限控制
  > 该项目的权限控制的拦截通过:src/fetch/api + vuex + router 去实现控制
  - 4.2 接口封装
  > 接口封装目录：src/fetch/api；

  > 在axios的基础上加上请求，响应拦截功能；

  > 在拦截基础上添加loading的显示的配置；

  > 在axios的基础上添加promise的回调方便调用.then .catch ；

  > 对axios的get 和 post 封装为 gAJAX 和 pAJAX , 需要其他方式自行封装；

  > 不同环境的请求地址配置：通过process.env.NODE_ENV 来实现；

  > 异步操作通过vuex dispatch；

  - 4.3 UI框架
  > antd；
- 5.其他
   - 5.1 特殊方法调用
   ```
   在vue.prototype 分别添加：
   $api;
   $staticData ;
   $http;
   $time;
   $utils;
   $isNum;
   $echarts;
   对象 ， 可以通过 例如：this.$api 的形式进行调用；
   ```

   - 5.2 关于vuex

   > 除了root模块的state ， commit ， action 外 增加了 ： fundManage 和 selectData 两个模块的state ，commit， action；

   - 5.3 关于router

   >页面是否需要执行init方法 通过设置 meta字段中的isInit 然后再 beforeEach钩子中进行判断；


<h2 id="chart">otcCharts</h2>

> 此部分省略

[点此查看源码](https://github.com/xorder-project/otcCharts)

<h2 id="web">官网</h2>

> 此部分省略

[点此查看源码](https://github.com/xorder-project/XorderWebsite)
