<template>
<!-- Card Music List -->
  <div class="container">
    <div v-if="isLoading" class="cards flex">
        <CardComponent v-for="(card) in cardList" :key="card.id" :cardDetails="card" />
    </div>

     <div v-else>
        <LoadingPage />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import CardComponent from './CardComponent.vue'
import LoadingPage from './LoadingPage.vue'

export default {
    name: 'CardList',
    components: {
        CardComponent,
        LoadingPage
    },

    data() {
        return {
            url: 'https://flynn.boolean.careers/exercises/api/array/music',
            cardList: [],
            isLoading: false
        }
    },

    methods: {
        getCardDetails() {
            axios.get(this.url).then((response) => {
                this.cardList = response.data.response; 
                setTimeout(() => {
                    this.isLoading = true;
                }, 1500);
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