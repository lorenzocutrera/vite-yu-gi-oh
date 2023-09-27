<script>
import axios from 'axios';

export default {
    components: {

    },
    data() {
        return {
            base_url : 'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0',
            cards: []
 
        }
    },
    created() { 

        console.log(this, this.base_url);
        /* axios.get returs a promis (una promessa... ti rispondo prima o poi) */
        axios
            .get(this.base_url)
            .then(response => {
                /* The request response is available in the then method */
                console.log(response); // the whole response object
                console.log(response.data); // the whole data response
                console.log(response.data.response);

                this.cards = response.data.response
            })
            .catch(error => {
                /* Handle a request error */
                console.log('Error:');
                console.error(error);
                this.error = error.message
            })


    }
}

</script>

<template></template>

<style scoped></style>
