 <template>
      <nav class="flex justify-between">
        <ul class="flex">
          <li class="p-5">
              <nuxt-link  to="/test">BlaBkla</nuxt-link>
          </li>
          <li class="p-5">
               <nuxt-link  to="/restaurants">Restaurant</nuxt-link>
          </li>
        </ul>
         <div class="flex">

          <!-- // If you are logged in -->
          <ul class="" v-if="username">
              <li class="p-5"><a href="#" class="uk-link-reset"><img src="https://png2.cleanpng.com/sh/a7adacc7226d2dc438dafb37913a8ab8/L0KzQYm3V8E2N5tqipH0aYP2gLBuTfVudZZ5ReZxZT3vdbj2Tf1wfppqRehyZHXyd7L0hb1xeppze9d8cz34frryigR1gV58Rdd2bXX3Pb3shB8udZD7gdc2NXK3coG9UMRibGJrfqI3Mkm0RoS7VMYyPWQ2TqY8M0m5R4GCUb5xdpg=/kisspng-emmet-the-lego-movie-videogame-princess-unikitty-w-emmet-lego-movie-5b4b0604ad1ff0.2916344615316433967091.png" class="uk-border-circle" height="40" width="40" alt="">{{ username }}</a></li>
              <li><a href="#" @click="logout">Logout</a></li>
          </ul>

          <!-- // If you are not logged in -->
          <ul class="flex" v-else>
              <li class="p-5"><a href="/users/register">Signup</a></li>
              <li class="p-5"><a href="/users/signin">Signin</a></li>
          </ul>

      </div>
      </nav>
 </template>

 <script>
    import { mapMutations } from 'vuex'

export default {  
  computed: {
    // Set your username thanks to your getter
    username() {
      return this.$store.getters['auth/username']
    }
  },
  methods: {
    // Define your needed mutations, here: auth/logout
    ...mapMutations({
      logout: 'auth/logout'
    })
  }
}
 </script>