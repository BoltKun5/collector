<template>
    <div class="quantity-change-button">
        {{modification}}{{amount}}
    </div>
</template>

<script>
    export default {
        props: {
            amount: Number,
            modification: {
                type: String,
                value: "+" | "-"
            }
        },
    }
</script>

<style lang="scss" scoped>
    .quantity-change-button {
        padding: 5px;
        background-color: rgb(185, 185, 255);
        border: darkslategray 2px solid;
        color: darkslategray;
        width: fit-content;
        font-weight: 400;
    }
</style>