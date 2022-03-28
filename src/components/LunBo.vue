<template>
  <div class="box">
    <ul>

    <van-swipe @change="onChange" :show-indicators="false" :width="105" :loop="false">
      <van-swipe-item v-for="(item, index) in attr" :key="index">
        <li>
          <div>
            <img :src="item.image" alt="" />
            <p class="name">{{ item.name }}</p>
            <p class="info">{{ item.info }}</p>
          </div>
        </li>
      </van-swipe-item>
    </van-swipe>
    </ul>
  </div>
</template>

<script>
export default {
  name: "LunBo",
  props: ["attr"],
  data() {
    return {
      current: 0,
    };
  },
  methods: {
    onChange(index) {
      this.current = index;
    },
  },
};
</script>

<style scoped>
.box ul {
  /* padding: 0 0.3076923076923077rem; */
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
.box ul li {
  display: flex;
  justify-content: space-between;
}
.box ul li div {
  margin-top: 0.24rem;
  width: 2.14rem;
  /* padding: 0 4px; */
  vertical-align: top;
}
.box ul li div img {
  width: 100%;
  height: 2.98rem;
}
.box ul li div p.name {
  margin-top: 0.12rem;
  color: #000028;
  font-size: 0.28rem;
  line-height: 0.4rem;
}
.box ul li div p.info {
  margin-top: 0.08rem;
  color: #a2a2b6;
  font-size: 0.24rem;
  line-height: 0.36rem;
  height: 0.36rem;
  overflow: hidden;
}
.van-swipe-item{
    margin-right: 0.24rem;
}
</style>