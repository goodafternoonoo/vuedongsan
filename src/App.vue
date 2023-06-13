<template>
    <div v-if="modalState" class="black-bg">
        <div class="white-bg">
            <h4>상세페이지</h4>
            <p>내용</p>
            <button @click="modalState = false">닫기</button>
        </div>
    </div>

    <div class="menu">
        <a v-for="menu in menus" :key="menu" href="#">{{ menu }}</a>
    </div>

    <div v-for="(product, i) in products" :key="i">
        <img :src="product.image" class="room-img" />
        <h4 @click="modalState = true">{{ product.title }}</h4>
        <p>월 {{ product.price.toLocaleString() }} 원</p>
        <button @click="product.count++">허위매물 신고</button>
        <span>신고수 : {{ product.count }}</span>
    </div>
</template>

<script>
import data from './assets/room';

export default {
    name: 'App',
    data() {
        return {
            modalState: false,
            menus: ['Home', 'Shop', 'About'],
            products: data,
        };
    },
    methods: {
        increase() {},
    },
    components: {},
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
}

body {
    margin: 0;
}

div {
    box-sizing: border-box;
}

.menu {
    background-color: darkslateblue;
    padding: 15px;
    border-radius: 5px;
}

.menu a {
    color: white;
    padding: 10px;
    text-decoration: none;
}

.room-img {
    width: 100%;
    margin-top: 40px;
}

.black-bg {
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    position: fixed;
    padding: 20px;
}

.white-bg {
    width: 100%;
    background-color: white;
    border-radius: 8px;
    padding: 20px;
}
</style>
