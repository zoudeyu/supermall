<template>
    <div class="goods">
        <goods-list-item v-for="item in goods" :goodsItem="item" :key="item.show.img"></goods-list-item>
    </div>
</template>

<script>

import GoodsListItem from './GoodsListItem'
export default {
    name: 'GoodsList',
    props: {
        goods: {
            type: Array,
            default: function() {
                return []
            }
        }
    },
    components: {
        GoodsListItem
    }

}
</script>

<style scoped>
    .goods{
        display: flex;
        flex-wrap: wrap;
        position: relative;
        justify-content: space-around;
    }
</style>