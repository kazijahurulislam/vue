<template>
  <div class="container">
    <form>
      <div class="form-group">
        <label for="Email1">Email address</label>
        <input v-model="login.email" type="email" class="form-control" id="Email1" placeholder="Email">
      </div>
      <div class="form-group">
        <label for="Password1">Password</label>
        <input v-model="login.pass" type="password" class="form-control" id="Password1" placeholder="Password">
      </div>
      <button v-if="seen" @click.prevent="loginfunc(login.email, login.pass)" type="submit" class="btn btn-default">LogIn</button>
    </form>
  </div>
</template>

<script>
  export default {
      name: 'login',
      data () {
          return {
              login: {
                email: null,
                pass: null
              },
              info: [],
              seen: true
          }
      },
      methods: {

        loginfunc: function (e,p) {
          axios.post('http://profile.authlab.io/api/v1/login', {
            email: e,
            password: p
          })
            .then(response => {
              this.info = response;
              console.log(response);
            })
            .catch(function (error) {
              console.log(error);
            });
        }
      }
  }
</script>

<style></style>
