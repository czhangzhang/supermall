<template>
  <div class="tab-control">
      <div v-for="(item,index) in titles" :key="index" class="tab-control-item" :class="{active:index === currentIndex}" @click="itemClick(index)">
          <span>{{item}}</span>
      </div>
  </div>
</template>

<script>
export default {
  name: "TabControl",
  props:{
      titles:{
          type:Array,
          default(){
              return []
          }
      }
  },
  data(){
      return {
          currentIndex:0,
      }
  },
  methods:{
      itemClick(index){
          this.currentIndex = index;
        //   由内向外发送自定义事件
          this.$emit('tabClick',index);
      }
  },
  components: {},
};
</script>

<style>
    .tab-control{
        display: flex;
        text-align: center;
        font-size: 16px;
        height: 40px;
        line-height: 40px;
        background-color: #fff;
    }
    .tab-control-item{
        flex: 1;
    }
    .tab-control-item span{
        padding: 5px;
    }
    .active{
        color:var(--color-high-text);
    }
    .active span{ 
        border-bottom: 3px solid var(--color-tint);
    }
</style>
