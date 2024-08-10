## LayUI - searchInput 组件


### 简介

SearchInput 组件。是一个搜索组件，输入完成后按回车键(Enter)提示选择过滤字段！按回退键(Backspace)删除内容和字段标签

### 效果

![示例图片](image/demo.png)

### 示例

```html
<!DOCTYPE HTML>
<html>
<head>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=Edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no"/>
  <meta name="format-detection" content="telephone=no" />
  <meta name="renderer" content="webkit">

  <!-- 运行sample时，请根据实际的layui库所处位置修改链接地址 -->
  <link rel="stylesheet" href="https://unpkg.com/layui@2.9.14/dist/css/layui.css">
  <link rel="stylesheet" href="./searchInput.css">
  <title>searchInput</title>
</head>
<body>
<div class="layui-container">
    <div class="layui-main">
      <fieldset class="layui-elem-field layui-field-title" id="demo1"><legend>演示</legend></fieldset>
      
      <div class="search-tag-container">
        <input type="text" class="search-tag-input" autocomplete="off" value="">
      </div>

      <div id="ID_tag"></div>
    </div>
  </div>
</div>
<!-- 运行sample时，请根据实际的layui库所处位置修改链接地址 -->
<script src="https://unpkg.com/layui@2.9.14/dist/layui.js"></script>
<script type="text/javascript">
  layui.config({
    base: '',
  });

  layui.use(['code', 'searchInput'], function(){
    layui.code();
    var $ = layui.$,
      searchInput = layui.searchInput;

    var searchInst = searchInput.render({
      elem: '.search-tag-input',
      title: '请选择查询字段',
      data: [//初始值
        {field: 'name', name: '名称'},
        {field: 'phone', name: '手机'},
        {field: 'sex', name: '性别'},
        {field: 'address', name: '地址'}
      ],
      keyNum: {
        remove: 8, //删除按键编号 默认，BackSpace 键
        create: 13 //创建按键编号 默认，Enter 键
      },
      beforeCreate: function (data, value) {//选择标签前操作，必须返回字符串才有效
        console.log('beforeCreate', arguments);
        return value;
      },
      onChange: function (data, value, type) {
        console.log('onChange', arguments);
        $('#ID_tag').text(JSON.stringify(value));
      }
    });

    // //获取数据方法
    // searchInst.clearTag();

  });
</script>
</body>
</html>
```