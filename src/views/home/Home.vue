<template>
  <div id="home">
    <nav-bar>
      <div slot="center" class="home-nav-bar">购物街</div>
    </nav-bar>
  </div>
</template>

<script>
  // 导入navbar
  import NavBar from "@/components/common/navbar/NavBar";
  // 导入api
  import { getHomeMultidata } from "network/home/home"

  export default {
    name: "Home",
    components: {
      NavBar
    },
    data() {
      return {
        banners: [],
        recommends: []
      }
    },
    created() {
      getHomeMultidata().then(result => {
        this.banners = result.data.banner;
        this.recommends = result.data.recommend;
      })
    },
  }
</script>

<style scoped>
  .home-nav-bar {
    background-color: var(--color-tint);
    color: white;
  }
</style>
