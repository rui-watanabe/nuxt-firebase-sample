<template>
 <div class="page">
   <p v-if="indicateUser.login">{{ indicateUser }}</p>
   <form
     v-else
     class="form"
     @submit.prevent
   >
     <label class="label">
       <span class="label">
         email
       </span>
       <input
         class="input"
         type="text"
         v-model="email"
       >
     </label>
     <label class="label">
       <span class="label">
         password
       </span>
       <input
         class="input"
         type="password"
         v-model="password"
       >
     </label>
     <button
       class="button"
       type="submit"
       @click="login"
     >
       Login
     </button>
   </form>
 </div>
</template>

<script>

export default {
 data() {
   return {
     email: '',
     password: ''
   }
 },
 computed: {
   indicateUser() {
     return this.$store.getters['getUser'];
   }
 },
 methods: {
  login() {
    this.$store.dispatch('loginAction', {
      email: this.email,
      password: this.password
    })
    if(this.$store.getters['getUser']) {
       this.$router.push('/home')
     }
   },
 }
}
</script>


