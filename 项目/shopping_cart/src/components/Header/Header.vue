<template>
    <!-- 标题组件 -->
    <div class="header-container">
        <h3>标题</h3>
    </div>
</template>

<script>
export default {
    name: 'MyHeader',

}
</script>

<style lang="less" scoped>
template {
    margin: 0;
    padding: 0;
}

.header-container {
    height: 45px;
    width: 100vw;
    background-color: #264e70;
    z-index: 2;
    h3 {
        font-size: 14px;
        color: #fff;
        text-align: center;
        line-height: 45px;
    }
}
</style>