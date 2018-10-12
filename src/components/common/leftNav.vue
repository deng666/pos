<template>
  <div id="leftnav" class="left-nav">
    <ul>
      <li>
        <i class="iconfont icon-goumai"></i>
        <div>收银</div>
      </li>
      <li>
        <i class="iconfont icon-dianpu"></i>
        <div>店铺</div>
      </li>
      <li>
        <i class="iconfont icon-hanbao"></i>
        <div>商品</div>
      </li>
      <li>
        <i class="iconfont icon-huiyuanqia"></i>
        <div>会员</div>
      </li>
      <li>
        <i class="iconfont icon-31daipingjia"></i>
        <div>统计</div>
      </li>
      <li>
        <i class="iconfont icon-gongnengjianyi"></i>
        <div>设置</div>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  name: 'leftnav'
}
</script>
<style scoped lang="less">
.left-nav {
  color: #fff;
  font-size: 14px;
  height: 100%;
  background-color: #1d8ce0;
  float: left;
  width: 5%;
  ul {
    padding: 0;
    margin: 0;
    li {
      list-style: none;
      text-align: center;
      border-bottom: 1px solid #666;
      padding: 10px;
      .iconfont {
        font-size: 20px;
      }
    }
  }
}
</style>
