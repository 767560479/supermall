<!--  -->
<template>
  <div id="home">
    <nav-bar class="home-nav">
      <div slot="center">购物车</div>
    </nav-bar>
    <home-swiper :banners="banners"></home-swiper>
    <recommend-view :recommends="recommends"></recommend-view>
  </div>
</template>

<script>
import NavBar from "components/common/navbar/NavBar";
import HomeSwiper from "./childComps/HomeSwiper";
import RecommendView from "./childComps/RecommendView";
import { getHomeMultidata } from "../../network/home";

export default {
  data() {
    return {
      banners: [],
      recommends: []
    };
  },
  components: {
    NavBar,
    HomeSwiper,
    RecommendView
  },
  //生命周期 - 创建完成（访问当前this实例）
  created() {
    getHomeMultidata().then(res => {
      this.banners = res.data.banner.list;
      this.recommends = res.data.recommend.list;
      console.log(this.banners);
      console.log(this.recommends);
    });
  },
  //生命周期 - 挂载完成（访问DOM元素）
  mounted() {},
  methods: {}
};
</script>
<style scoped>
/* @import url(); 引入css类 */

.home-nav {
  background-color: var(--color-tint);
  color: #fff;
}
</style>