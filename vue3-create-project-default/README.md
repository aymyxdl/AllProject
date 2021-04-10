# json-server

这里使用 json-server 充当服务器
启动命令 json-server --watch db.json

如果本地无法启动，试着全局安装再启动
db.json是数据库


# less-loader

在 .vue 文件中的 style标签中使用 less 语法

<script lang="less" scoped>
.a {
  .b {
    .c {
      .d {
        display: flex
      }
    }
  }
}
</script>

npm i -D less-loader@7.0.1