<template>
    <div class="d-flex justify-center">
        <v-card width="600px" class="mt-12 pa-10">
            <v-card-title>
                Создайте аккаунт
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

            <v-text-field
                label="Введите желаемое имя:"
                v-model="name"
                outlined
            ></v-text-field>

            <v-text-field
                label="Ваш сайт:"
                v-model="website"
                outlined
            ></v-text-field>

            <v-text-field
                label="Электронный адрес для связи:"
                v-model="email"
                outlined
            ></v-text-field>

            <v-text-field
                label="Город:"
                v-model="city"
                outlined
            ></v-text-field>

            <v-text-field
                label="Город:"
                v-model="company"
                outlined
            ></v-text-field>

            <!--input v-model="password" type = "password"-->
            <v-btn @click="register">
                Создать!
            </v-btn>
        </v-card>
    </div>
</template>

<script>
export default {
  name: 'register',
  props: {
   /* msg: String*/
  },
  data(){
  return {
  login: "",
  password: "",
  name : "",
  website : '',
  email : '',
  city : '',
  company : ''
  };
  },
  methods: {
  register(){
  this.axios.get('http://188.225.47.187/api/jsonstorage/107088275edd7ca5850406e669197382').then(
  (response)=> {
    let users = response.data;
    users.push({login : this.login, password : this.password, name : this.name, website : this.website, email : this.email, city : this.city, company : this.company});
    this.axios.put('http://188.225.47.187/api/jsonstorage/107088275edd7ca5850406e669197382', users).then();
    this.$emit('register', {data : users[users.length() - 1], id : users.length() - 1});
  }
  );
  }
  }
}
</script>