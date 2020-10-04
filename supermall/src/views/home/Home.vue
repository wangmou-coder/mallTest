<template>
  <div id="home">
    <!-- <h2>首页</h2> -->
    <NavBar class="nav-home">
      <div slot="center">购物街</div>
    </NavBar>
    <HomeSwiper :banner = "banner"></HomeSwiper>
  </div>
</template>

<script>
  import NavBar from '@/components/common/navbar/NavBar'
  // import Swiper from '@/components/common/swiper/Swiper'
  // import SwiperItem from '@/components/common/swiper/SwiperItem'
  import HomeSwiper from './childComps/HomeSwiper'
  import {
    getHomeMultidata
  } from '@/network/home'
  export default {
    name: 'home',
    components: {
      NavBar,
      HomeSwiper
    },
    data() {
      return {
        banner: [],
        recommend: []
      }
    },
    created() {
      getHomeMultidata().then(res => {
        // console.log(res);
        this.banner = res.data.banner.list
        this.recommend = res.data.recommend.list
      })
    },
  }

</script>

<style>
  .nav-home {
    background-color: var(--color-tint);
    color: white;
  }

</style>
