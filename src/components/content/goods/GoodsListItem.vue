<template>
    <div class="goods-list-item">
        <img :src="goodsItem.show.img" alt="">
        <div>
            <p class="goods-info">{{goodsItem.title}}</p>
            <span class="price">{{goodsItem.price}}</span>
            <span class="collect">{{goodsItem.cfav}}</span>
        </div>
    </div>
</template>

<script>
export default {
    name: 'GoodsListItem',
    props: {
        goodsItem: {
            type: Object,
            default(){
                return {}
            }
        }
    }
}
</script>


<style scoped>
    .goods-list-item{
        display: inline-block;
        width: 45vw;
        position: relative;
    }
    .goods-list-item img {
        width: 100%;
        border-radius: 5px;
    }

    .goods-list-item .goods-info {
        font-size: 14px;
        overflow: hidden;
        text-overflow: ellipsis;
        white-space: nowrap;
    }

</style>