<template>
    <div v-if="modalState" class="black-bg">
        <div class="white-bg">
            <img :src="rooms[selectedId].image" class="room-img" />
            <h4>{{ rooms[selectedId].title }}</h4>
            <p>{{ rooms[selectedId].content }}</p>
            <p>월 {{ rooms[selectedId].price.toLocaleString() }}원</p>
            <input v-model="month" />개월
            <p>총 {{ (rooms[selectedId].price * month).toLocaleString() }}원</p>
            <button @click="closeModal">닫기</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'CommonModal',
    data() {
        return {
            month: 1,
        };
    },
    watch: {
        month(data, prev) {
            if (data > 12) {
                alert('12개월까지만 입력할 수 있습니다.');
                this.month = prev;
            }
        },
    },
    props: {
        rooms: Array,
        selectedId: Number,
        modalState: Boolean,
    },
    methods: {
        closeModal() {
            this.$emit('closeModal');
        },
    },
};
</script>

<style></style>
