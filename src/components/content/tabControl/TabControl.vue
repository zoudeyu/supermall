<template>
    <div class="tab-bar">
        <div  class="tab-bar-item" v-for="(item,index) in titles" :key="item">
            <span :class="{isActive: currentIndex === index}" @click="itemClick(index)" >{{item}}</span>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TabControl',
    props: {
        titles: {
            type: Array,
            default: function () {
                return []
            }
        }
    },
    data: function () {
        return {
            currentIndex: 0
        }
    },
    methods: {
        itemClick(index){
            console.log('aaa')
            this.currentIndex = index
            this.$emit('tabBarClick',index)
        }
    }
}
</script>

<style scoped>
    .tab-bar {
        display: flex;
        text-align: center;
        font-size: 15px;
    }

    .tab-bar-item {
        flex: 1;
        height: 40px;
        line-height: 40px;
    }

    .tab-bar-item  span{
        padding: 5px;
    }

    .tab-bar-item  .isActive {
        color: var(--color-high-text);
        border-bottom: 2px solid var(--color-tint);
    }

</style>