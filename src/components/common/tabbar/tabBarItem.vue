<template>
    <div class="tab-bar-item" @click="clickMethod">
        <div :class="{active: isActive}" :style="{color: isActive ? activeColor: ''}">
            <slot name="img-content"></slot>
            <slot name="text"></slot>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TabBarItem',
    methods: {
        clickMethod(){
            console.log(this.path)
            this.$router.replace(this.path)
        }
    },
    props: {
        path: {
            type: String
        },
        activeColor: {
            type: String,
            default: 'red'
        }
    },
    computed: {
        isActive: {
            get: function () {
                return this.$route.path.indexOf(this.path) !== -1
            }
        }
    }
}
</script>

<style scoped>
    .tab-bar-item {
        flex: 1;
        text-align: center;
        height: 49px
    }

    .tab-bar-item .img-content {
        width: 24px;
        height: 24px;
        background-color: gray;
        margin: 0 auto;
    }

    .tab-bar-item .active {
        color: red;
    }

    .tab-bar-item .active .img-content{
        background-color: red;
    }
</style>