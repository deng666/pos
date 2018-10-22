<template>
  <div>
    <div v-show="isActive" v-for="love in item.love" :key="love.id">{{love.name}}</div>
    <div style="color: red" @click="toggle()" v-if="item.love.length > 1">{{text}}</div>
  </div>
</template>

<script>
  export default {
    props: ['item'],
    data() {
      return {
        isActive: false
      }
    },
    methods: {
      toggle() {
        this.isActive = !this.isActive
      }
    },
    computed:{
      text:function(){
        if(this.isActive == false){//对文字进行处理
          return '展开'
        }else{
          return '收起'
        }
      }
    }
  }
</script>