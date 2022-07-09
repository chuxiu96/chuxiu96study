<template>
    <div class="app-container">
        <!-- 头部区域 -->
        <my-header></my-header>

        <!-- 循环渲染每个商品的信息 -->
        <my-goods
            v-for="item in list"
            :key="item.id"
            :goodsId="item.id"
            :goodsState="item.goods_state"
            :goodsImg="item.goods_img"
            :goodsTitle="item.goods_name"
            :goodsPrice="item.goods_price"
            :goodsCount="item.goods_count"
            @countChange="getNewState"
        ></my-goods>

        <my-footer
            :isFull="fullState"
            :amount="getAmount"
            :totalCount="total"
            @full-change="getFullState"
        ></my-footer>
    </div>
</template>

<script>
// 导入 axios 请求库
import axios from 'axios'
// 导入 eventBus
import bus from './components/eventBus'

// 导入组件
import MyHeader from './components/Header/Header.vue'
import MyGoods from './components/Goods/Goods.vue'
import MyFooter from './components/Footer/Footer.vue'

export default {
    name: 'MyApp',
    data () {
        return {
            list: []
        }
    },
    created () {
        // 调用请求数据的方法
        this.initCartList()
        bus.$on('share', (val) => {
            this.list.some(item => {
                if (item.id === val.id) {
                    item.goods_count = val.value
                    return true
                }
            })
        })
    },
    methods: {
        // 封装请求列表数据的方法
        async initCartList () {
            // 调用 axios GET 方法，请求数据
            const { data: res } = await axios.get(
                'https://www.escook.cn/api/cart'
            )
            this.list = res.list
        },
        // 监听 input 数据变化
        getNewState (e) {
            this.list.some(item => {
                if (item.id === e.id) {
                    item.goods_state = e.value
                    // 终止循环
                    return true
                }
            })
        },
        // 监听 footer 是否全选
        getFullState (e) {
            this.list.forEach(item => item.goods_state = e)
        }
    },
    computed: {
        // 动态计算商品是否全选
        fullState () {
            return this.list.every(item => item.goods_state === true)
        },

        // 动态计算商品总价
        getAmount () {
            return this.list.filter(item => item.goods_state).reduce((totalAmount, singleItem) => {
                return totalAmount += singleItem.goods_price * singleItem.goods_count
            }, 0)
        },

        //   已勾选商品的总数量 
        total () {
            return this.list.filter(item => item.goods_state).reduce((total, item) => {
                return total += item.goods_count
            }, 0)
        }
    },
    components: {
        MyHeader,
        MyGoods,
        MyFooter
    }
}
</script>

<style lang="less">
@import './css/index.css';
</style>