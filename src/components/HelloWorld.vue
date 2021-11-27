<template>
  <div class="hello">
    <h1>简单欢迎一下</h1>
    <p>
    相关代码在Github仓库中点击这里进行引导<br>
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-alert</a>.
    </p>
    <h3>Installed</h3>
    <ul>
      <li><a target="_blank" rel="noopener">npm i vue-simple-alert --save</a></li>
    </ul>
    <h3>相关功能在About中</h3>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
