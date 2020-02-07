<template>
    <div class="d-flex justify-center">
        <v-card width="600px" class="mt-12 pa-10">
            <v-card-title>
                Войдите в аккаунт
            </v-card-title>
            <v-text-field
                label="Введите логин"
                v-model="login"
                outlined
            ></v-text-field>
            <!--input v-model="login" type =  "text"-->

            <v-text-field
                label="Введите пароль"
                v-model="password"
                outlined
            ></v-text-field>
            <!--input v-model="password" type = "password"-->
            <v-btn @click="authenticate">
                Войти
            </v-btn>
        </v-card>
    </div>
</template>

<script>
export default {
  name: 'login',
  props: {
   /* msg: String*/
  },
  data(){
  return {
  login: "",
  password: ""
  };
  },
  methods: {
  authenticate(){
  this.axios.get('http://188.225.47.187/api/jsonstorage/107088275edd7ca5850406e669197382').then(
  (response)=> {
    let users = response.data;
    let found = -1;
    for (let el in users) {
        if (this.login == users[el].login && this.password == users[el].password) {
        this.$emit('login', {data : users[el], id : el});
        this.$router.push('/users/'+ el);
        found = el;
        break;
        }
    }
    if (found == -1) {
        window.alert('bad login/password');
    }
  }
  );
  }
  }
}
</script>