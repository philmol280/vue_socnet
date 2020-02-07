<template>
  <div id="app">
<v-app>
      <v-app-bar shrink-on-scroll absolute color="#ffb69f" src = "https://i.pinimg.com/originals/f7/9d/1f/f79d1faa3cd97ab3df901e2a4f716a7d.jpg" light dense app>

      </v-app-bar>
    <v-navigation-drawer app color="blue-grey lighten-4" dark expand-on-hover hide-overlay permanent mini-variant-width="38px">
        <div id="nav">
            <v-list nav dense shaped>
                <v-list-item><router-link to="/" >Home   </router-link></v-list-item>
                <v-list-item><router-link to="/about" >About  </router-link> </v-list-item>
                <v-list-item><router-link to="/login">Login   </router-link> </v-list-item>
                <v-list-item><router-link to="/register" >Registration</router-link> </v-list-item>
            </v-list>
        </div>
    </v-navigation-drawer>
      <v-content app>
        <v-container app fluid>
          <router-view login="logInto" @register="regUser"/>
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
  id : '-1',
  userData : {}
  };
  },
  methods : {
  logInto(obj) {
    this.userData = obj.data;
    this.id = obj.id;
  },
  regUser(obj) {
    this.userData = obj.data;
    this.id = obj.id;
  }
  }
}
</script>
