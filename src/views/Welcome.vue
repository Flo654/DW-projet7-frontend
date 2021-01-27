<template>
  <section role="region" aria-label="connection" class="welcome container">
    <div>
      <img src="../assets/logo.png" alt="logo entreprise" width="200" >
    </div>
    <div v-if="showLogin" >
      <h1 >Se connecter</h1>
      <LoginForm @login="goToMainVue" />
      <p>Pas encore de compte ? <span @click="showLogin = false">creez le</span> alors !</p>
    </div>
    <div v-else >
      <h1>Creer un compte</h1>
      <SignupForm />
      <p>Déja un compte <span @click="showLogin =true">Connectez vous !</span></p>
      
    </div>
     
    
  </section>
</template>

<script>
import SignupForm from '../components/SignupForm.vue'
import LoginForm from '../components/LoginForm.vue'
import { ref } from 'vue'
import { useRouter } from 'vue-router'

export default {
  components: { SignupForm, LoginForm },
  setup() {
    const showLogin = ref(true)
    const router = useRouter()

    const goToMainVue = ()=>{
      
      router.push({ name: 'MainVue'})

    }

    return{ showLogin, goToMainVue }
  }
}
</script>

<style>

body{
  background: rgb(219, 216, 216);
}
  .welcome {
    
    text-align: center;
    padding: 20px 0;
  }
  /* form styles */
  .welcome form {
    width: 11rem;
    margin: 20px auto;
  }
  .welcome label {
    display: block;
    margin: 20px 0 10px;
  }
  .welcome input {
    width: 100%;
    padding: 10px;
    border-radius: 20px;
    border: 1px solid #eee;
    outline: none;
    color: #999;
    margin: 10px auto;
  }
  .welcome span{
    font-weight: bold;
    text-decoration: underline;
    cursor: pointer;
  }
  .welcome button {
    margin: 20px auto;
  }
  .welcome h1{
    font-size: 1.4rem;
  }
</style>