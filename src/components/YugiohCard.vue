<script>

export default {
    name: 'YugiohCards',
    props: {
        card_name: String,
        card_img: String,
    }
}

</script>

<template>
    <img :src="card_img" />
    {{ card_name }}
</template>

<style scoped></style>
