<template>
  <div class="home">
    <v-card v-for="item in obj" :key="item"
    class="mx-auto"
    shaped>
      <v-list-item-avatar><img :src=item.avatar></v-list-item-avatar>
      <v-list-item-content class="font-weight-black">
                        <v-list-item-title> {{item.company}} </v-list-item-title>
                        <v-list-item-subtitle>{{item.name}} </v-list-item-subtitle>
      </v-list-item-content>
    </v-card>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'home',
  data() { return {obj : {}};},
  components: {
  },
  mounted() {
   this.axios.get('http://188.225.47.187/api/jsonstorage/107088275edd7ca5850406e669197382').then(
  (response)=> {
  this.obj = response.data;
  }
  );
  }
}
</script>
