
<script>
const axios = require('axios');

/* eslint-disable */

export default {
  name: 'Header',

  data() {
    return {
      wordsearch: ''
    }
  },

  created(){
    this.searchDrink();
  },

  methods: {

    //? Metodo de Busca
    searchDrink: function() {

      this.$parent.loading = true;

      this.getDrinks(drinks => {
          
        this.getIngredients(drinks, drinksFiltered => {
          this.$parent.drinks = drinksFiltered;
          this.$parent.loading = false;
        });  

      });
    },

    //? resgata os drinks na API 
    getDrinks: function(callback){
      axios
        .get('https://www.thecocktaildb.com/api/json/v1/1/search.php?s=' + this.wordsearch)
        .then(function(response){
          callback(response.data.drinks);
        }); 
    },

    //? Organiza os ingredientes em um array 
    getIngredients: function(drinks, callback){

      let qtyIngredients, ingredients;

      drinks = drinks.map( drink => {
        qtyIngredients = 15;
        ingredients = [];
        
        while(qtyIngredients > 0){
          if(drink['strIngredient' + qtyIngredients])
            ingredients.push(drink['strIngredient' + qtyIngredients]);
          qtyIngredients--;
        }

        drink.ingredients = ingredients;
        return drink;
      });

      callback(drinks);
    }

  },

};
</script>

<template>
  <header>

    <div class="container">

      <div class="header__logo">
        <router-link to="/"><i></i></router-link>
      </div>
      
      <div class="header__search">
        <i></i>
        <input type="text" v-model="wordsearch" @keyup="searchDrink" placeholder="Search for Products, Brands and More">
      </div>

    </div>

  </header>
</template>

<style scoped lang="scss">
@import "@/assets/sass/components/header.scss";
</style>
