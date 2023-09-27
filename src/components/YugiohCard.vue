<script>

export default{
    name: 'YugiohCards',
    props: {
        card_name: String,
        card_img :String,
    }
}

</script>

<template>
    
        {{ card_name }}
        <img :src="card_img" />


</template>

<style scoped></style>
