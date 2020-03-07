<template>
  <div id="app">
<v-app>
    <v-navigation-drawer app color="blue-grey lighten-4" expand-on-hover hide-overlay permanent mini-variant-width="100px" right>
        <div id="nav">
            <v-list nav dense shaped>
                <v-list-item  two-line>
                    <v-list-item-avatar><img :src=userData.avatar></v-list-item-avatar>
                    <v-list-item-content class="font-weight-black">
                        <v-list-item-title> {{userData.company}} </v-list-item-title>
                        <v-list-item-subtitle>{{userData.name}} </v-list-item-subtitle>
                    </v-list-item-content>
                </v-list-item>
                <v-divider class="my-3"></v-divider>
                <v-list-item link to="/"><v-list-item-icon><v-icon>mdi-home-outline</v-icon></v-list-item-icon><v-list-item-content><v-list-item-title>Home   </v-list-item-title></v-list-item-content></v-list-item>
                <v-list-item  link to="/about"> <v-list-item-icon><v-icon>mdi-alpha</v-icon></v-list-item-icon><v-list-item-content> <v-list-item-title>About  </v-list-item-title> </v-list-item-content> </v-list-item>
                <v-list-item  link to="/login"> <v-list-item-icon><v-icon> mdi-account-arrow-right</v-icon> </v-list-item-icon><v-list-item-content> <v-list-item-title>Login   </v-list-item-title> </v-list-item-content></v-list-item>
                <v-list-item  link to="/register"><v-list-item-icon> <v-icon>mdi-account-arrow-left-outline</v-icon></v-list-item-icon><v-list-item-content><v-list-item-title>Registration</v-list-item-title> </v-list-item-content> </v-list-item>
                <v-list-item link :to=id><v-list-item-icon><v-icon>mdi-account-circle</v-icon></v-list-item-icon><v-list-item-content><v-list-item-title>Profile </v-list-item-title></v-list-item-content></v-list-item>
            </v-list>
        </div>
    </v-navigation-drawer>
      <v-app-bar app shrink-on-scroll absolute color="#ffb69f" src = "https://i.pinimg.com/originals/f7/9d/1f/f79d1faa3cd97ab3df901e2a4f716a7d.jpg" light dense >

      </v-app-bar>
      <v-content class="px-10 py-15">
        <v-container app fluid>

          <router-view @login="logInto" :userData="userData" @register="regUser" @logout="logOut"/>
        </v-container>
      </v-content>
</v-app>
  </div>
</template>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #ff35aa;
    padding: 10px;
    text-decoration: none;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>

<script>

export default {
  name: 'App',
  components: {

  },
  data(){
  return {
  id : '/users/-1',
  userData : {}
  };
  },
  methods : {
  logInto(obj) {
    this.userData = obj.data;
    this.id = "/users/" + obj.id;
  },
  regUser(obj) {
    this.userData = obj.data;
    this.id = "/users/" + obj.id;
  },
  logOut(){
    this.userData = {};
    this.id = "/users/-1";
  }
  }
}
</script>
