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
          <ul class="flex align-center" v-if="username">
              <li class="p-5">
                <a href="#" class="uk-link-reset">{{ username }}</a>
                </li>
              <li class="p-5">
                <a href="#" @click="logout">Logout</a>
              </li>
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