<template>
  <div>
    <div class="banner">
      <van-swipe @change="onChange">
        <van-swipe-item v-for="(item, index) in head" :key="index">
          <img :src="item.image" alt="" />
          <p>{{ item.txt }}</p>
        </van-swipe-item>
        <template #indicator>
          <div class="custom-indicator">{{ current + 1 }}/4</div>
        </template>
      </van-swipe>
    </div>

     <div class="floor1">
        <p class="title_top">热门推荐</p>
        <ul>
            <li v-for="(item,index) in floor1" :key="index">
                <div>
                    <img :src="item.image" alt="">
                    <p class="name">{{item.name}}</p>
                    <p class="info">{{item.info}}</p>
                </div>

            </li>
        </ul>
    </div>

    <div class="floor2">
        <p class="title_top">每日推荐</p>
        <LunBo :attr="floor2"></LunBo>
        
    </div>

    <div class="floor3">
        <p class="title_top">下饭短剧</p>
        <LunBo :attr="floor3"></LunBo>
    </div>

    

  </div>
</template>
<script>
import axios from 'axios'
import LunBo from '../components/LunBo.vue'
export default {
  name: "MyDianShiJu",
  data(){
      return{
          current: 0,
          head:null,
          floor1:null,
          floor2:null,
          floor3:null
      }
  },
  methods: {
    onChange(index) {
      this.current = index;
    },
    async getData(){
        let {data} = await axios.get("/api/dianshiju")
        this.head = data.head
        this.floor1 = data.floor1
        this.floor2 = data.floor2
        this.floor3 = data.floor3
    }
  },
  components:{
    LunBo
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
    font-size: 0.3461538461538462rem;
    line-height: 0.4230769230769231rem;
    font-weight: 700;
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
.floor2,.floor3{
    padding: 0.24rem 0.32rem 0;
}
</style>
