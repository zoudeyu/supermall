<template>
    <div id="home">
        <nav-bar class="home-nav"><template slot="navCenter">首页</template></nav-bar>
        <home-swiper :banners="banners"/>
        <recommend-view :recommends='recommends'></recommend-view>
    </div>
</template>

<script>

import NavBar from '../../components/common/navbar/NavBar'
import {getHomeMultidata} from '../../network/home'
import HomeSwiper from './childrenComps/HomeSwiper'
import RecommendView from './childrenComps/RecommendView'

export default {
    name: 'Home',
    components: {
        NavBar,
        HomeSwiper,
        RecommendView
    },
    data: function(){
        return {
            banners: [],
            recommends: []
        }
    },
    created() {
        console.log('created')
        getHomeMultidata().then(res => {
            console.log(res)
            this.banners = res.data.banner.list
            this.recommends = res.data.recommend.list
        })
    }
}



</script> 

<style scoped>
    .home-nav {
        background-color: var(--color-tint);
        color: white;
    }
</style>