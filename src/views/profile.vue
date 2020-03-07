<template>
  <div class="home">
      <div v-if="logged">
     <v-row class="text-left">
            <v-col cols="10">
                <h1 class="green--text text--darken-2">
                    <v-icon large color="green darken-2">mdi-account-outline</v-icon>
                    {{userData.name}}
                </h1>
            </v-col>
        </v-row>
        <v-row class="text-left">
            <v-col cols="2">
                <img :src=userData.avatar style="max-width: 100%">
            </v-col>
            <v-col cols="10" class="text-left">
                <p>
                    Web-site: <a href=userData.website target="_blank">{{userData.website}}</a>
                </p>
                <p>
                    E-mail: <a href="mailto:...">{{userData.email}}</a>
                </p>
                <p>
                    City: {{userData.city}}
                </p>
                <p>
                    Working company: {{userData.company}}
                </p>
            </v-col>
        </v-row>
          <v-btn @click="logout">Logout</v-btn>
      </div>
      <div v-if="!logged">
          <v-row>
              <p class="text-left">You are not in any account</p>
          </v-row>
          <v-row>
              <p class="text-left"> visit <router-link to="/login"> Login page </router-link> to sign in or <router-link to="/register"> Register page </router-link> to sign up</p>
          </v-row>
      </div>

  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'profile',
  props: ['userData'],
  data() {
  return {logged : false};},
  mounted(){
  this.logged = (this.$route.params.id != '-1');
  },
  watch: {$route(){
  this.logged = (this.$route.params.id != '-1');
  }},
  components: {
  },
  methods: {
  logout() {
  this.$emit('logout');
  this.logged = false;
  this.$router.push('/');
  }
  }
}
</script>
