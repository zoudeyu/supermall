<template>
    <div class="nav-bar">
        <div class="left"><slot name="navLeft"></slot></div>
        <div class="center"><slot name="navCenter"></slot></div>
        <div class="right"><slot name="navRight"></slot></div>
    </div>
</template>

<script>
export default {
    name: 'NavBar'
}
</script>

<style scoped>
    .nav-bar {
        display: flex;
        line-height: 44px;
        text-align: center;
        box-shadow: 0 1px 1px rgba(100,100,100,0.1);
    }

    .nav-bar .left,.right {
        width: 60px;
    }

    .nav-bar .center {
        flex: 1;
    }
</style>