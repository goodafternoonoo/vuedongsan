<template>
    <Transition name="fade">
        <CommonModal
            :rooms="rooms"
            :selectedId="selectedId"
            :modalState="modalState"
            @closeModal="closeModal"
        />
    </Transition>

    <div class="menu">
        <a v-for="menu in menus" :key="menu" href="#">{{ menu }}</a>
    </div>

    <DiscountBanner />

    <RoomCard
        v-for="(room, i) in rooms"
        @openModal="openModal($event)"
        @report="report(i)"
        :key="i"
        :room="room"
    />
</template>

<script>
import data from './assets/room';
import DiscountBanner from './components/DiscountBanner.vue';
import CommonModal from './components/CommonModal.vue';
import RoomCard from './components/RoomCard.vue';

export default {
    name: 'App',
    data() {
        return {
            menus: ['Home', 'Shop', 'About'],
            rooms: data,
            modalState: false,
            selectedId: 0,
        };
    },
    methods: {
        openModal(id) {
            this.selectedId = id;
            this.modalState = true;
        },
        closeModal() {
            this.modalState = false;
        },
        report(id) {
            this.rooms[id].count++;
        },
    },
    components: {
        DiscountBanner,
        CommonModal,
        RoomCard,
    },
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

.discount {
    background-color: #eee;
    padding: 10px;
    margin: 10px;
    border-radius: 5px;
}

.fade-enter-from {
    transform: translateY(-1000px);
}
.fade-enter-active {
    transition: all 0.5s;
}
.fade-enter-to {
    transform: translateY(0px);
}

.fade-leave-from {
    opacity: 1;
}
.fade-leave-active {
    transition: all 1s;
}
.fade-leave-to {
    opacity: 0;
}
</style>
