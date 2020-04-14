<template>
  <article id="app">
    <Nav />
    <Logo id="logo" />
    <router-view/>
    <Footer />
  </article>
</template>

<script>
// @ is an alias to /src
import Logo from '@/components/Logo.vue'
import Nav from "@/components/Navbar.vue"
import Footer from "@/components/Footer.vue"
export default {
  name: "App",
  components: {
    Nav,
    Logo,
    Footer
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  z-index: 0;
}



#logo{
  position: sticky;
  top: 5px;
  left: 5px;
  z-index: 99;
  display: flex;
}


#nav {
  z-index: 1;
  position: sticky;
  top: 0;
  padding: 25px;
  margin: 0;
}

#nav a {
  font-weight: bold;
 
}

#nav a:hover{
  color: rgb(112, 102, 124);
}

#nav a.router-link-exact-active {
  color: #ffa600de;
}


.mar{
  max-width: 700px;
  display: inline-block;
}
</style>
