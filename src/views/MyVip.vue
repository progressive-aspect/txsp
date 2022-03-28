<template>
  <div>
    <MyLunBo :attr="attr"></MyLunBo>
    <div class="mod_user_info">
      <div class="top flex_v_justify">
        <div class="user_info flex_vc">
          <div class="user_wrap">
            <img
              class="img"
              src="https://puui.qpic.cn/vupload/0/20190710_1562730875638_zvh5l5pj2id.png/0"
            />
          </div>
          <div class="info">
            <div class="flex_vc">
              <div class="name">未登录</div>
              <img
                class="vip-icon"
                src="https://puui.qpic.cn/vupload/0/20190822_0_grey_3x.png/0"
              />
            </div>
            <div class="date">登录后查看你的VIP频道</div>
          </div>
        </div>
        <div class="actImg">
          <img src="https://vc.qpic.cn/pictest/mtvivppbThkCL.png" />
        </div>
      </div>
    </div>
    <div class="tuijian">
      <p class="title_top">今日推荐专属</p>
      <LunBo :attr="tuijian"></LunBo>
    </div>
    <div class="flex_cs">
      <span>电视剧</span>
      <span>电影</span>
      <span>动漫</span>
      <span>全部分类</span>
    </div>
    <div class="floor1">
      <p class="title_top">正在热播</p>
      <ul>
        <li v-for="(item, index) in rebo" :key="index">
          <div>
            <img :src="item.image" alt="" />
            <p class="name">{{ item.name }}</p>
            <p class="info">{{ item.info }}</p>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
import MyLunBo from "../components/MyLunBo.vue";
import LunBo from "../components/LunBo.vue";
import axios from "axios";
export default {
  name: "MyVip",
  data() {
    return {
      attr: null,
      tuijian: null,
      rebo:null,
    };
  },
  components: {
    MyLunBo,
    LunBo,
  },
  methods: {
    async getData() {
      let { data } = await axios.get("/api/VIP");
      console.log(data);
      this.attr = data.swiper;
      this.tuijian = data.tuijian;
      this.rebo = data.rebo
    },
  },
  created() {
    this.getData();
  },
};
</script>
<style lang="less" scoped>
.top {
  background: #f6f8fa;
}
.flex_v_justify {
  display: flex;
  align-items: center;
  justify-content: space-evenly;
  padding: 0 0.32rem;
}
.flex_vc {
  display: flex;
  .img {
    width: 0.88rem;
    height: 0.88rem;
    margin-right: 0.2rem;
  }
}
.info {
  font-size: 0.3rem;
  .vip-icon {
    width: 0.45rem;
    height: 0.3rem;
  }
  .date {
    font-size: 0.26rem;
    color: #ccc;
  }
}
.actImg {
  img {
    width: 2.8rem;
    height: 1.4rem;
  }
}
.tuijian {
  padding: 0.24rem 0.32rem 0;
}
.flex_cs {
  margin-top: 0.5rem;
  margin-bottom: 0.5rem;
  border-radius: 5rem;
  background: #f6f8fa;
  color: #d6ab56;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
  font-size: 0.26rem;
  span {
    padding: 0.3rem 0;
  }
}
.floor1{
    padding-left: 0.3076923076923077rem;
    padding-right:  0.3076923076923077rem;
}
.floor1 ul{
    /* padding: 0 0.3076923076923077rem; */
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
}
.floor1 ul li{
    display: flex;
    justify-content: space-between;
}
.floor1 ul li div{
    margin-top: 0.24rem;
    /* padding: 0 4px; */
    vertical-align: top;
}
.floor1 ul li div img{
    width: 100%;
    height: 1.88rem;
}
.floor1 ul li div p.name{
    margin-top: 0.12rem;
    color: #000028;
    font-size: 0.28rem;
    line-height: 0.4rem;
}
.floor1 ul li div p.info{
    margin-top: 0.08rem;
    color: #a2a2b6;
    font-size: 0.24rem;
    line-height: 0.36rem;
}
</style>
