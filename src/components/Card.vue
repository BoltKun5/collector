<template>
    <div class="single-card">
        <img src="../assets/cards/14.png">
    </div>
</template>

<script>
    export default {
        props: {
            img: {
                type: String,
                default: "/assets"
            }
        }
    }
</script>

<style lang="scss" scoped>
    .single-card {
        background: red;
    }
</style>