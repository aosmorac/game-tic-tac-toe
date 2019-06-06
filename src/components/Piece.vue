<template>
    <div class="piece-content" @click="clickHandler" v-text="symbol"></div>
</template>
<script>
    export default {
        name: 'piece',
        props: {
            symbol: {
                type: String,
                default: ''
            }
        },
        methods: {
            clickHandler() {
                this.$emit("tap")
            }
        }
    }
</script>
<style lang="scss" scoped>
    @import url('https://fonts.googleapis.com/css?family=Luckiest+Guy&display=swap');
    $luckiest-guy: 'Luckiest Guy', cursive;

    .piece-content{
        height: 100%;
        width: 100%;
        font-family: $luckiest-guy;
        color: lime;
        font-size: 100px;
    }
</style>