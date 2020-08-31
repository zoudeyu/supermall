<template>
    <div class="wrapper" :style="{height: propWidth}" ref="scroll">
        <div class="content">
            <slot></slot>
        </div>    
    </div>    
</template>

<script>
import bscroll from 'better-scroll'
export default {
    name: 'Scroll',
    data: ()=>{
        return {
            scroll: null
        }
    },
    props: {
        propWidth: {
            type: String,
            default: 'calc(100bh - 93px)'
        },
        probeType: {
            type: Number,
            default: 0
        },
        pullUpload: {
            type: Boolean,
            default: true
        }
    },
    mounted:function () {
        this.scroll = new bscroll(this.$refs.scroll,{
            click: true,
            probeType: this.probeType,
            pullUpLoad: this.pullUpload
        }),
        // 监听滚动位置
        this.scroll.on('scroll',(position) => {
            this.$emit('scrollPosition',position)
        })

        // 监听上拉事件
        this.scroll.on('pullingUp', () => {
            console.log('上')
            this.$emit('betterScroll')
        })
    }
}
</script>
    
<style scoped>
    .wrapper {
        position: fixed;
    }
</style>