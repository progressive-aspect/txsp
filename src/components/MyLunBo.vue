<template>
  <div class="header">
    <!-- <van-swipe :autoplay="3000">
      <van-swipe-item v-for="(item, index) in attr" :key="index">
        <img :src="item" alt="" />
      </van-swipe-item>
    </van-swipe> -->
    <van-swipe class="my-swipe" :autoplay="3000" indicator-color="white" width="7.14rem">
      <van-swipe-item v-for="(item,index) in attr" :key="index">
        <img :src="item" alt="">
      </van-swipe-item>
    </van-swipe>
  </div>
</template>
<script>
export default {
  name: "MyLunBo",
  props: ["attr"],
  methods:{
     fn(){
       console.log(this.name)
    }
  },
  created(){
    this.fn()
  }
};
</script>
<style scoped>
.my-swipe{
  width: 7.14rem;
  padding: 0 .18rem;
  overflow: hidden;
}
.my-swipe .van-swipe-item img{
  width: 7.14rem;
}
</style>