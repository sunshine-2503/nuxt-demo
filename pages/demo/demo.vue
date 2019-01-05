<template>
  <div>
    <h2>{{title}}</h2>

    <br><br>
    <el-button @click="visible = true">点我</el-button>
    <el-dialog :visible.sync="visible" title="Hello world">
      <p>Try Element</p>
    </el-dialog>

    <br><br>
    <a href="/" class="button--green">主页</a>
    <a href="/test/test" class="button--grey">TEST</a>

  </div>
</template>

<script>
  export default {
    name: 'demo',

    data() {
      return {
        title: '测试',
        visible: false,
        issue: {}
      }
    },

    mounted: function() {
      this.getApiData();
    },

    methods: {
      getApiData: function() {
        //设置请求路径
        const url = 'http://wd.apiplus.net/newly.do?token=t0248909c3620ff1bk&code=cqssc&format=json'
        // 发送请求:将数据返回到一个回到函数中
        const _this= this;
        // 并且响应成功以后会执行then方法中的回调函数
        this.$axios.get(url).then(function(result) {
          // result是所有的返回回来的数据
          // 包括了响应报文行
          // 响应报文头
          // 响应报文体
          console.log(result);
          _this.issue = result;
        });
      }
    }
  }
</script>

<style scoped>

</style>
