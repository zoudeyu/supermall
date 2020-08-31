<template>
    <div id="home">
        <nav-bar class="home-nav"><template slot="navCenter">首页</template></nav-bar>
        <home-swiper :banners="banners"/>
        <recommend-view :recommends='recommends'></recommend-view>
        <feature-vue />
        <tab-control :titles="titles" class="tab-control" @tabBarClick="handleBarClick"></tab-control>
        <goods-list :goods="goods[Object.keys(goods)[currentIndex]].list"></goods-list>
    </div>
</template>

<script>

import HomeSwiper from './childrenComps/HomeSwiper'
import RecommendView from './childrenComps/RecommendView'
import FeatureVue from './childrenComps/FeatureVue'

import NavBar from '../../components/common/navbar/NavBar'
import TabControl from  '../../components/content/tabControl/TabControl'
import GoodsList from '../../components/content/goods/GoodsList'

import {getHomeMultidata,getHomeGoods} from '../../network/home'

export default {
    name: 'Home',
    components: {
        NavBar,
        HomeSwiper,
        RecommendView,
        FeatureVue,
        TabControl,
        GoodsList
    },
    data: function(){
        return {
            banners: [],
            recommends: [],
            titles: ['流行','新款','精选'],
            goods: {
                'pop': {page: 0, list: []},
                'new': {page: 0, list: []},
                'sell': {page: 0, list: []},
            },
            currentIndex:0
        }
    },
    created() {
        this.getHomeMultidata()

        // 请求商品数据
        this.getHomeGoods('pop')
        this.getHomeGoods('sell')
        this.getHomeGoods('new')
    },
    methods: {
        /**
         * 网络请求相关
         */
        getHomeMultidata(){
            getHomeMultidata().then(res => {
                console.log(res)
                this.banners = res.data.banner.list
                this.recommends = res.data.recommend.list
            })
        },
        getHomeGoods(type){
            const page = this.goods[type].page + 1;
            getHomeGoods(type,page).then(res => {
                console.log(res);
                this.goods[type].list.push(...res.data.list);
                this.goods[type].page += 1
            })
        },
        /**
         * 事件监听相关的方法
         */
        handleBarClick(index){
            console.log(index)
            this.currentIndex = index
        }
    }
}



</script> 

<style scoped>
    #home {
     padding: 44px 0px 49px;   
    }
    .home-nav {
        background-color: var(--color-tint);
        color: white;
        position: fixed;
        left: 0;
        right: 0;
        top: 0;
        z-index: 1;
    }

    .tab-control {
        position: sticky;
        top: 44px;
        background-color: white;
        z-index: 9;
    }
</style>