<template>  
  <div>

       <!-- Search input to filters restaurants -->
      <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">

          <input class="bg-white focus:outline-none focus:shadow-outline border border-gray-300 rounded-lg py-2 px-4 block w-full appearance-none leading-normal" v-model="query" type="search" placeholder="Search...">
      </form>

       <!-- Restaurant cards -->
      <div class="max-w-sm rounded overflow-hidden shadow-lg" v-for="(restaurant, index) in filteredList" v-bind:key="index">     
              <img :src="'http://localhost:1337/' + restaurant.Images.url" alt="" class="w-full">    
          <div class="px-6 py-4">
                  <h3 class="font-bold text-xl mb-2">{{ restaurant.Name }}</h3>
                  <p class="text-gray-700 text-base">{{ restaurant.Description }}</p>
                  <!-- // Link to the restaurant using router-link -->
                  <router-link :to="{ Name: 'restaurant-id', params: { id: restaurant.id }}" tag="a" class="bg-teal-500 hover:bg-teal-600 focus:outline-none focus:shadow-outline">See dishes
                  </router-link>
          </div>
      </div>

      <!--  If no restaurants have been found -->
      <div class="container" v-if="filteredList.length == 0">
       <img src="https://assets-ouch.icons8.com/preview/19/52de2377-696e-4194-8c63-0a81aef60b4f.png" height="800" width="800">
       <p>No restaurants found</p>
     </div>

  </div>

</template>

<script>  
// Import the restaurants query
import restaurantsQuery from '~/apollo/queries/restaurant/restaurants'

export default {  
  data() {
    return {
      // Initialize an empty restaurants variabkle
      restaurants: [],
      query: ''
    }
  },
  apollo: {
    restaurants: {
      prefetch: true,
      query: restaurantsQuery
    }
  },
  computed: {
    // Search system
    filteredList() {
      return this.restaurants.filter(restaurant => {
        return restaurant.Name.toLowerCase().includes(this.query.toLowerCase())
      })
    },
  }
}
</script>  