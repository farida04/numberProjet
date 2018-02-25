<template>
  <div class="login">
      <img id='logo' src="./../assets/numbers.svg" alt="">
      <form>
          <input class='connect' type="text" name="pseudo" placeholder="pseudo" required>
          <input class='connect' type="password" name="password" placeholder="mot de passe" required>
          <router-link to='/menu'>
              <input id='btn' type="submit" name="connexion" placeholder="connexion">
         </router-link>
      </form>
      <router-link to='/inscription'>
      <p id="new"> <span id="blue">Pas de compte? </span> Nouvel Utilisateur</p>
      </router-link>
  </div>
</template>

<script>
export default {
  name: 'Login',
  // data () {
  //   return {
  //     msg: 'Welcome to Your Vue.js App'
  //   }
  // }
}
</script>


<style scoped>

#logo{
    width: 270px;
    height: 270px;
    position: absolute;
    top: 5px;
    left: 30px;
}

form{
    position: absolute;
    top:280px;
}

.connect{
     display: block;
     margin: 0 30px;
     border: none;
     width: 70vw;
     height: 40px;
     border-bottom: 3px solid #44A5A5;
     text-align: center;
     font-size: 1.5em;
 }

 #btn{
     border: none;
     background: none;
     border: 3px solid #E41D1A;
     width: 80%;
     height: 60px;
     background: #44A5A5;
     color: #fff;
     margin: 50px 35px;
     font-size: 2em;
     border-radius: 20px;
 }
 #new{
     position: absolute;
     top: 500px;
     left: 55px;
     font-size: 1em;
     color: dimGray;
 }
 #blue{
     color: DeepSkyBLue;
 }
</style>
