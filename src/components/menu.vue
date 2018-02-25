<template>
     <div id="index">
         <header>
             <img id='logo' src="./../assets/logo.svg">
             <img id='menu' src="./../assets/menu.svg">
             <hr>
         </header>
         <article >
             <router-link to='/duel'>
                 <input type='submit' class='type2' value="Nouvelle Partie">
             </router-link>
             <router-link to='/infos'>
                 <input type='submit' value='Mes Stats' >
             </router-link>
             <router-link to=''>
                 <input type='submit' class='type2' value="Utilisateurs Connectés">
             </router-link>
             <router-link to=''>
                 <input type='submit' value="Tchat">
             </router-link>
         </article>

     </div>
</template>

<script>
export default{
    name: 'Menu',
}
</script>

<style scoped>
#menu{
    position: absolute;
    width: 60px;
    height: 60px;
    right: 20px;
    top: 22px;
}
#logo{
    width: 100px;
    height: 100px;
    position: absolute;
    top: 0;
}
link{
    text-decoration: none;
}


hr{
    height: 10px;
    background: #44A5A5;
    color: #44A5A5;
    position: relative;
    top: 80px;
}

input{
    background: #44A5A5;
    margin: 5px 25px;
    font-size: 1.5em;
    width: 80vw;
    height: 70px;
    color: #fff;
    border-radius: 10px;
    text-decoration: none;
}


.type2{
    background: #E41D1A;
}

article{
    position: absolute;
    top: 150px;
}
</style>
