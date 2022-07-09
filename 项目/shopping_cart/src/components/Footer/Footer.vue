<template>
    <div class="wrapper">
        <div class="footer-container">
            <span class="checkState">
                <input
                    type="checkbox"
                    id="cbFull"
                    :checked="isFull"
                    @change="fullChange"
                >
                <label for="cbFull">全选</label>
            </span>
            <span class="payment">
                <span>合计: ￥ {{ amount.toFixed(2) }}</span>
            </span>
            <button class="check-button">结算（ {{ totalCount }} ）</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'MyFooter',
    props: {
        isFull: {
            type: Boolean,
            default: true
        },
        amount: {
            type: Number,
            default: 0
        },
        // 已勾选商品总数量
        totalCount: {
            type: Number,
            default: 0
        }
    },
    emits: ['full-change'],
    methods: {
        fullChange (e) {
            this.$emit('full-change', e.target.checked)
        }
    },
}
</script>

<style lang="less" scoped>
.wrapper {
    position: fixed;
    bottom: 0;
    background-color: #fff;
}
.footer-container {
    position: relative;
    width: 100vw;
    height: 40px;
}
.checkState {
    margin: 0 5px;
    line-height: 40px;
    label {
        padding-left: 10px;
    }
}

.payment {
    margin: 0 40px;
}

.check-button {
    position: absolute;
    right: 10px;
    margin-top: 2.5px;
    width: 100px;
    height: 35px;
    background-color: rgb(50, 139, 240);
    color: #fff;
    text-align: center;
    border-radius: 40px;
    border: 0px;
}
</style>