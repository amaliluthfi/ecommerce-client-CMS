<template>
  <div class="login mt-5" style="padding=10px">
    <h1 >Login Form</h1>

<!--card login -->
    <div class="center mt-5 mb-5" >
      <b-card
      header="Login"
      header-bg-variant="dark"
      header-tag="header"
      title="Fill in th blank"
    >
<!--login form -->
    <form @submit.prevent="login()">
     <div class="mb-3 row">
       <label for="staticEmail" class="col-sm-2 col-form-label" style="font-family= 'lato'" >Email</label>
       <div class="col-sm-10">
          <input type="email" class="form-control" id="inputEmail" v-model="payload.email">
       </div>
     </div>
     <div class="mb-3 row">
       <label for="inputPassword" class="col-sm-2 col-form-label" >Password</label>
       <div class="col-sm-10">
         <input type="password" class="form-control" id="inputPassword" v-model="payload.password">
     </div>
     </div >
     <b-button  type="submit" variant="primary">Submit</b-button>
    </form>
    </b-card>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Login',
  data () {
    return {
      payload: {
        email: '',
        password: ''
      }
    }
  },
  computed: {

  },
  methods: {
    login () {
      this.$store.dispatch('login', this.payload)
      this.$store.commit('changePage', 'dashboard')
    }
  },
  beforeRouteEnter (to, from, next) {
    if (localStorage.access_token) {
      next('/dashboard')
    } else {
      next()
    }
  }
}
</script>

<style  scoped>
.login {
  text-align: center;
  color: #4d6f91;
  background-color: #eeeeee;
}

h1 {
  font-family: 'fraunces', serif;
}

p {
  font-family: 'lato', sans-serif;
}

b-card {
  font-family: 'lato', serif;
}

.center {
  margin: auto;
  width: 35%;
  padding: 10px;
}
</style>
