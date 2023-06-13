<template>
    <div>
        <img :src="room.image" class="room-img" />
        <h4 @click="openModal">
            {{ room.title }}
        </h4>
        <p>월 {{ room.price.toLocaleString() }}원</p>
        <button @click="$emit('report')">허위매물 신고</button>
        <span>신고수 : {{ room.count }}</span>
    </div>
</template>

<script>
export default {
    name: 'RoomCard',
    props: {
        room: Object,
    },
    methods: {
        openModal() {
            this.$emit('openModal', this.room.id);
        },
    },
};
</script>

<style></style>
