<script>
import YugiohCard from './YugiohCard.vue';
import axios from 'axios';

export default {
    name: 'AppMain',
    components: {
        YugiohCard
    },
    data() {
        return {
            base_url: 'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0',

            cards: {},

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

                this.cards = response.data.data;
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

<template>
    <div class="container">

        <div class="cont">
            <div class="row d-flex">
                <div v-for="card in cards" class="col">
                    <div class="card">
                        <YugiohCard :card_img="card.card_images[0].image_url" :card_name="card.name"></YugiohCard>
                    </div>
                </div>
            </div>

        </div>
    </div>
</template>

<style lang="scss" scoped>
.col {
    width: calc(100% / 5);

    .cont {
        background-color: white;
    }

    .card {
        background-color: #d59038;
        border: none;
        text-align: center;
        padding: 5px;
    }
}
</style>