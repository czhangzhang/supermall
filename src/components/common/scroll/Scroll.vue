<template>
  <div class="wrapper" ref="wrapper">
    <div class="content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
import BScroll from "better-scroll";
export default {
  name: "Scroll",
  props:{
    probeType:{
      type:Number,
      default:0
    },
    pullUpLoad:{
      type:Boolean,
      default:false
    }
  },
  data() {
    return {
      scroll: null,
    };
  },
  mounted() {
    // 创建滚动对象
    this.scroll = new BScroll(this.$refs.wrapper, {
        click:true,
        probeType:this.probeType,
        pullUpLoad:this.pullUpLoad
    });
    // 监听滚动事件
    this.scroll.on('scroll',(position)=>{
      this.$emit('scroll',position)
    })
    // 监听上拉加载更多
    this.scroll.on('pullingUp',()=>{
      // console.log('上拉加载更多');
      this.$emit('pullingUp')
    })
  },
  methods:{
    scrollTo(x,y,time=500){
      this.scroll.scrollTo(x,y,time=500);
    },
    finishPullUp(){
      this.scroll.finishPullUp()
    }
  },
  components: {},
};
</script>

<style></style>
