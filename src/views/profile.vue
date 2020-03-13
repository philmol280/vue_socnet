<template>
  <div class="home">
      <div v-if="logged">
          <div v-if="!edit">
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
              <v-btn v-if="typeof userData['login'] !== 'undefined' " @click='edit = true'>Edit profile data</v-btn>
          </div>
          <div v-if="edit">
               <v-text-field
                label="Сменить имя"
                v-model="userData.name"
                outlined
            ></v-text-field>

            <v-text-field
                label="Сменить сайт"
                v-model="userData.website"
                outlined
            ></v-text-field>

            <v-text-field
                label="Сменить email"
                v-model="userData.email"
                outlined
            ></v-text-field>

            <v-text-field
                label="Изменить город"
                v-model="userData.city"
                outlined
            ></v-text-field>

            <v-text-field
                label="Изменить компанию"
                v-model="userData.company"
                outlined
            ></v-text-field>

            <v-text-field
                label="Ссылка на аватарку"
                v-model="userData.avatar"
                outlined
            ></v-text-field>
              <v-btn @click="send">Apply changes</v-btn>
          </div>
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
  return {logged : false, edit : false};},
  mounted(){
  this.logged = (this.$route.params.id != '-1');
  this.edit = false;
  },
  watch: {$route(){
  this.logged = (this.$route.params.id != '-1');
  this.edit = false;
  }},
  components: {
  },
  methods: {
  logout() {
  this.$emit('logout');
  this.logged = false;
  this.$router.push('/');
  },
  send() {
  this.axios.get('http://188.225.47.187/api/jsonstorage/107088275edd7ca5850406e669197382').then(
  (response)=> {
    let users = response.data;
    users[Number(this.$route.params.id)] = this.userData;
    this.axios.put('http://188.225.47.187/api/jsonstorage/107088275edd7ca5850406e669197382', users);
  }
  );
  }
  }
}
</script>
