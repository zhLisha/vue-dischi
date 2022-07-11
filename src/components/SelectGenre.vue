<template>
    <label class="flex" for="genre"> 
      <span>FILTRA PER GENERI</span>
      <select v-model="selectedGenre" @change.prevent="changeGenre()" name="genre" id="genre">
        <option disabled selected>Generi</option>
        <option value="All">All</option>
        <option value="Rock">Rock</option>
        <option value="Pop">Pop</option>
        <option value="Jazz">Jazz</option>
        <option value="Metal">Metal</option>
      </select>
    </label>
</template>

<script>
export default {
    name: 'SelectGenre',
    data() {
      return {
        selectedGenre: "All"
      }
    },

    props: {
      musicGenre: Object
    },

    methods: {
      changeGenre() {
        // this.selectedGenre = "";
    
        this.$emit('selectGenre', this.selectedGenre)
      }
    }
}
</script>

<style lang="scss" scoped>
@import '@/style/variables.scss';

label {
  flex-direction: column;
  align-items: center;
  
  span {
    padding-bottom: 20px;
    color: $mainTextColor;
    font-size: 20px;
  }

  select {
  padding: 5px 80px 5px 0;
  width: 30%;
}
}
</style>