<template>
    <view class="index">
        <view>
            我的
        </view>
    </view>
    <nut-tabbar :v-model="2" bottom placeholder safe-area-inset-bottom @tab-switch="tabSwitch">
        <nut-tabbar-item v-for="(item, _index) in state.list" :tab-title="item.title" :icon="item.icon"> </nut-tabbar-item>
    </nut-tabbar>
</template>

<script lang="ts" setup>
import { Category, Home, My } from '@nutui/icons-vue-taro';
import Taro from '@tarojs/taro';
import { h, reactive } from 'vue';

const state = reactive({
    list: [
        {
            title: '首页',
            icon: h(Home),
            name: 'home'
        },
        {
            title: '分类',
            icon: h(Category),
            name: 'category'
        },
        {
            title: '我的',
            icon: h(My),
            name: 'my'
        }
    ]
})

const tabSwitch = (item, index) => {
    console.log(item, index);
    if (index == 0) {
        Taro.switchTab({
            url: '/pages/index/index'
        })
    } else if (index == 1) {
        Taro.switchTab({
            url: '/pages/category/index'
        })
    } else if (index == 2) {
        Taro.switchTab({
            url: '/pages/my/index'
        })
    }
}

</script>

<style lang="scss">
.index {
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 40px;
    color: #ff0000;
}
</style>
