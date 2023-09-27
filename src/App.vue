<script>
import axios from 'axios';

export default {
    data() {
        return {
            cards: []

        }
    },
    mounted() {
        console.log('hi there');

        console.log(axios);
        /* axios.get returs a promis (una promessa... ti rispondo prima o poi) */
        axios
            .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0')
            .then(response => {
                /* The request response is available in the then method */
                console.log(response); // the whole response object
                console.log(response.data); // the whole data response
                console.log(response.data.response);

                this.cards = response.data.response
            })
            .catch(error => {
                /* Handle a request error */
                console.log(error);
                console.log(error.message);
                this.error = error.message
            })


    }
}

</script>

<template></template>

<style scoped></style>
