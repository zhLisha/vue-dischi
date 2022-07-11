<template>
  <div class="flex input-wrapper">
    <!-- Filter by Music Genre -->
    <label class="flex" for="genre"> 
      <span>FILTRA PER GENERI</span>
      <select v-model="selectedGenre" @change.prevent="changeGenre()" name="genre" id="genre">
        <option disabled selected>Genre</option>
        <option value="All Genre">All Genre</option>
        <option value="Rock">Rock</option>
        <option value="Pop">Pop</option>
        <option value="Jazz">Jazz</option>
        <option value="Metal">Metal</option>
      </select>
    </label>

    <!-- Filter by Author -->
    <label class="flex author" for="author">
      <span>FILTRA PER AUTORE</span>
      <select v-model="selectedAuthor" id="author" name="author" @change.prevent="changeAuthor()" >
        <option disabled selected>Authors</option>
        <option value="All Authors">All Authors</option>
        <option v-for="(author, index) in authorsArr" :key="index"  :value="author.author">{{author.author}}</option>
      </select>
    </label>
  </div>
</template>

<script>
export default {
    name: 'SelectGenre',
    data() {
      return {
        selectedGenre: "All Genre",
        selectedAuthor: "All Authors"
      }
    },

    props: {
      authorsArr: Array
    },

    methods: {
      changeGenre() {
        this.$emit('selectGenre', this.selectedGenre)
        console.log(this.selectedGenre);
      },

      changeAuthor() {
        this.$emit('selectAuthor', this.selectedAuthor)

        console.log(this.selectedAuthor);
      }
    }
}
</script>

<style lang="scss" scoped>
@import '@/style/variables.scss';

.input-wrapper {
  justify-content: space-evenly;

  label {
    flex-direction: column;
    align-items: center;
    
    span {
      padding-bottom: 20px;
      color: $mainTextColor;
      font-size: 20px;
    }

    select {
    padding: 5px 150px 5px 0;
    width: 30%;
    }
  }
}

</style>