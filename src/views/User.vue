<template>
  <div class="addLink">
    <router-link :to="{name:'add'}">添加新闻</router-link>
  </div>
</template>

<script>
export default {
  name: "User"
}
</script>


<style scoped lang='scss'>
.addLink{
  text-align: center;
}
</style>
