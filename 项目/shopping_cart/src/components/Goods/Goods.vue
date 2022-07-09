<template>
    <!-- 商品列表组件 -->
    <div class="goods-container">
        <div class="goods-content">
            <div class="thumb">
                <div class="custom-control custom-checkbox">
                    <input
                        type="checkbox"
                        class="custom-control-input"
                        :id="'cb' + goodsId"
                        :checked="goodsState"
                        @change="stateChange"
                    >
                    <label
                        :for="'cb' + goodsId"
                        class="custom-control-label"
                    >
                        <div class="goods-img">
                            <img
                                :src="goodsImg"
                                alt="商品图片"
                            >
                        </div>
                    </label>
                </div>
            </div>
            <div class="good-title">
                <span class="">{{ goodsTitle }}</span>
            </div>
            <!-- 商品价格 -->
            <div class="good-price">￥ {{ goodsPrice }} </div>
            <!-- 商品数量 -->
            <MyCounter :id="goodsId" :counter_goodsCount="goodsCount"></MyCounter>
        </div>
    </div>
</template>

<script>
import MyCounter from '../Counter/Counter.vue'

export default {
    name: 'MyGoods',
    // props: ['goodsImg', 'goodsTitle', 'goodsPrice'],
    props: {
        goodsId: {
            required: true,
            type: Number
        },
        goodsImg: String,
        goodsTitle: {
            default: "商品名称",
            type: String
        },
        goodsPrice: Number,
        goodsState: {
            default: true,
            type: Boolean
        },
        goodsCount: {
            type: Number,
            default: 1
        }
    },
    emits: ['countChange'],
    methods: {
        stateChange (e) {
            const newState = e.target.checked
            // 触发自定义事件
            this.$emit('countChange', { id: this.goodsId, value: newState })
        }
    },
    components: {
        MyCounter
    }
}
</script>

<style lang="less" scoped>
.goods-content {
    position: relative;
    width: 100vw;
    height: 125px;
    border-bottom: 2px solid rgba(205, 205, 205, 0.5);
}

.thumb {
    display: block;
    width: 25px;
}

.thumb input {
    position: absolute;
    top: 50%;
    margin-top: -6.5px;
}

.goods-img {
    position: absolute;
    top: 0;
    left: 15px;
    display: inline-block;
    width: 125px;
    height: 125px;
}

.good-title {
    position: absolute;
    top: 5px;
    left: 10px;
    margin-left: 140px;
    font-size: 13px;
    font-weight: 700;
}

.good-price {
    position: absolute;
    left: 150px;
    bottom: 5px;
    color: red;
    font-weight: 700;
}
</style>