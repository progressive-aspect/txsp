<template>
  <div class="jingxunaBox">
    <div class="banner">
      <van-swipe @change="onChange">
        <van-swipe-item v-for="(item,index) in head" :key="index">
          <img :src="item.image" alt="">
          <p>{{item.txt}}</p>
        </van-swipe-item>
        <template #indicator>
          <div class="custom-indicator">{{ current + 1 }}/4</div>
        </template>
      </van-swipe>
    </div>

    <div class="floor">
        <p class="title_top">猜你喜欢</p>
        <ul>
            <li v-for="(item,index) in floor" :key="index">
                <div>
                    <img :src="item.image" alt="">
                    <p class="name">{{item.name}}</p>
                    <p class="info">{{item.info}}</p>
                </div>

            </li>
        </ul>
    </div>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  name: "MyJingXuan",
  data() {
    return {
      current: 0,
      head:null,
      floor:null
    };
  },
  methods: {
    onChange(index) {
      this.current = index;
    },
    async getData(){
        let {data} = await axios.get("/api/jingxuan")
        this.head = data.head
        this.floor = data.floor
    }
  },
  created(){
      this.getData()
  }
};
</script>
<style scoped>
.banner{
    margin-bottom: 0.3461538461538462rem;
    padding: 0 0.3076923076923077rem;
    background-image: -webkit-linear-gradient(90deg,#f2f4f5,#fff 59%);
}
.banner img{
    height: 3.846153846153846rem;
}
.banner p{
    padding: 0.25rem 0;
    font-size: 0.2692307692307692rem;
    line-height: 0.3846153846153846rem;
}
.custom-indicator {
    position: absolute;
    right: 5px;
    bottom: 0.2884615384615385rem;
    padding: 2px 5px;
    font-size: 0.3461538461538462rem;
}
.title_top{
    padding-left: 0.3076923076923077rem;
    font-size: 0.3461538461538462rem;
    line-height: 0.4230769230769231rem;
    font-weight: 700;
}
.floor ul{
    padding: 0 0.3076923076923077rem;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
}
.floor ul li{
    display: flex;
    justify-content: space-between;
}
.floor ul li div{
    margin-top: 12px;
    /* padding: 0 4px; */
    vertical-align: top;
}
.floor ul li div img{
    width: 100%;
    height: 1.88rem;
}
.floor ul li div p.name{
    margin-top: 0.12rem;
    color: #000028;
    font-size: 0.28rem;
    line-height: 0.4rem;
}
.floor ul li div p.info{
    margin-top: 0.08rem;
    color: #a2a2b6;
    font-size: 0.24rem;
    line-height: 0.36rem;
}
</style>
