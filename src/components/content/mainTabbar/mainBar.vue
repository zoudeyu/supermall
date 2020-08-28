<template>
    <tab-bar>
        <tab-bar-item path="/home">
            <template slot="img-content"><div class="img-content"></div></template>
            <template slot="text"><div>首页</div></template>
        </tab-bar-item>
        <tab-bar-item path='/category'>
            <template slot="img-content"><div class="img-content"></div></template>
            <template slot="text"><div>分类</div></template>
        </tab-bar-item>
        <tab-bar-item path='/cart' activeColor="purple">
            <template slot="img-content"><div class="img-content"></div></template>
            <template slot="text"><div>购物车</div></template>
        </tab-bar-item>
        <tab-bar-item path="/profile">
            <template slot="img-content"><div class="img-content"></div></template>
            <template slot="text"><div>我的</div></template>
        </tab-bar-item>
    </tab-bar>
</template>

<script>
import tabBar from '../../common/tabbar/tabBar'
import tabBarItem from '../../common/tabbar/tabBarItem'
export default {
    name: 'MainBar',
    components: { 
        tabBar,
        tabBarItem
    }
}
</script>