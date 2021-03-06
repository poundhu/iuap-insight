# iuap-insight

端到端数据采集整体方案

## 快速使用

将项目中 src 目录下的`iuap-insight.js`使用script标签引入，如需使用压缩版取 lib 目录下文件即可（最简单方式，直接引入我们提供的资源CDN地址即可）。然后，进行初始化工作即可实现无痕埋点，自动上报数据：

```
<script>
    uis.start({
      trackerUrl: 'your server path',
      userId: '1511676',
      siteId: 'csj',
    });
  </script>
```

配置说明：

- `trackerUrl` : 后台监听url  
- `userId`: 用户id  
- `siteId`: 站点id

## 进阶使用

- 如需手动设置，可以这样：

```
<div id="app" style="background:#ccc;"> 点我发送 </div>

<script src="http://design.yonyoucloud.com/static/jquery/3.2.1/jquery.js"></script>
<script type="text/javascript" src="./iuap-insight.js"></script>

<script>
  uis.start({
    trackerUrl: 'xxx',
    userId:'1511676',
    siteId:'csj',
  });

  $('#app').click(function(e){
    uis.track(e, 'click_text', '设置的信息')
  })
</script>
```


## 更多方法

- `uis.trackJqueryAjax($)` : 监听jquery的ajax事件，参数为jquery对象。需要先引入jquery，才能调用此方法。
- `uis.log({ext1:'xxx',ext2:'xxx'})` : 用户自定义日志信息，开发者在需要记日志的地方调用此方法，参数只能是: ext1,ext2 ... ext5。
- `uis.track(name, value)`
- `uis.setOption(name, value)`
- `uis.getOption(name)`
- 其他 API 请查看 UIS 对象


## TODO 状态


- [x] `click_text` 字段信息统计，主动设置 `track` 时不统计默认的 `trackClicks` 所提供的信息。
- [x] `error_msg` 字段，`js` 报错的时候，提交的统计信息（给定固定的文案进行信息统计）
- [ ] 未引用 `jq` 的时候未统计到信息（待下次版本进行方案处理），目前使用 `.tranckJqueryAjax($)` 这个 API 之前需要提前引入 jquery ，并且使用了 $.ajax 。
- [x] track API 使用文档更新
