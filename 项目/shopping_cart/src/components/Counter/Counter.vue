<template>
    <div class="number-container">
        <!-- 减一的按钮 -->
        <button type="button" @click="sub">-</button>
        <!-- 购买的数量 -->
        <span>{{ counter_goodsCount }}</span>
        <!-- 加一的按钮 -->
        <button type="button" @click="add">+</button>
    </div>
</template>

<script>
import bus from '../eventBus'

export default {
    name: 'MyCounter',
    props: {
        id: {
            type: Number,
        },
        counter_goodsCount: {
            type: Number,
            default: 1
        }
    },
    methods: {
        add() {
            const obj = {
                id: this.id,
                value: this.counter_goodsCount + 1
            }
            
            bus.$emit('share', obj)
        },

        sub() {
            if (this.counter_goodsCount === 0) {
                return
            }
            const obj = {
                id: this.id,
                value: this.counter_goodsCount - 1
            }
            
            bus.$emit('share', obj)
        }
    },
}
</script>

<style lang="less" scoped>
.number-container {
    position: absolute;
    right: 25px;
    bottom: 10px;

    button {
        width: 25px;
        height: 25px;
    }

    span {
        display: inline-block;
        width: 30px;
        height: 25px;
        text-align: center;
    }
}
</style>