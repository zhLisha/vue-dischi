<template>
<!-- Card Music List -->
  <div class="container">
    <div class="cards flex">
    <CardComponent v-for="(item, index) in cardList" :key="index" :cardDetails="item" />
  </div>
  </div>
</template>

<script>
import axios from 'axios';
import CardComponent from './CardComponent.vue'

export default {
    name: 'CardList',
    components: {
        CardComponent
    },

    data() {
        return {
            url: 'https://flynn.boolean.careers/exercises/api/array/music',
            cardList: []
        }
    },

    methods: {
        getCardDetails() {
            axios.get(this.url).then((response) => {
                this.cardList = response.data.response; 
            });
        }
    },

    created() {
        this.getCardDetails();
    }
}
</script>

<style lang="scss" scoped>
.cards {
    flex-wrap: wrap;
    padding: 70px 0;
}

</style>