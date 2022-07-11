<template>
<!-- Card Music List -->
  <div class="container">
    

    <!-- Cards -->
    <div v-if="isLoading" >
        <!-- Option Chose by Genre -->
        <div class="select-genre">
            <SelectGenre @selectGenre="currentGenre" @selectAuthor="currentAuthor" :authorsArr="cardList"/>
        </div>
        <div class="cards flex">
            <CardComponent v-for="(card) in filteredSong" :key="card.id" :cardDetails="card" />
        </div>
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
import SelectGenre from './SearchSelect.vue'

export default {
    name: 'CardList',
    components: {
        CardComponent,
        LoadingPage,
        SelectGenre
    },

    data() {
        return {
            url: 'https://flynn.boolean.careers/exercises/api/array/music',
            cardList: [],
            isLoading: false,
            searchedGenre: 'All Genre',
            searchedAuthor: 'All Authors'
        }
    },

    computed: {
        filteredSong() {
            if(this.searchedGenre === 'All Genre' && this.searchedAuthor === 'All Authors') {
                return this.cardList;
            } else if(this.searchedGenre !== 'All Genre' && this.searchedAuthor === 'All Authors') {
                 return this.cardList.filter((element) => {
                    return element.genre.includes(this.searchedGenre)
                });
            } else if(this.searchedAuthor !== 'All Authors' && this.searchedGenre === 'All Genre'){
                return this.cardList.filter((element) => {
                    return element.author.includes(this.searchedAuthor)
                });
            }

            return this.cardList.filter((element) => {
                return element.genre.includes(this.searchedGenre) && element.author.includes(this.searchedAuthor)
            })
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
        },

        currentGenre(genre) {
            this.searchedGenre = genre;
        },

        currentAuthor(author) {
            this.searchedAuthor = author;
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
    padding: 50px 0;
}

.select-genre {
    padding-top: 50px;
}

</style>