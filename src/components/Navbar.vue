<template>
  <header class="navbar expand">
    <nav id="nav" class=" py-3 bg-primary text-info">
      <router-link to="/" class="nav-link">Home</router-link> 
      <router-link to="/project" class="nav-link">Project</router-link> 
      <router-link to="/about" class="nav-link">Over</router-link>
      <router-link to="/contact" class="nav-link">Contact</router-link>
    </nav>
  </header>
</template>

<script>
export default {
  name: "Navbar"
}
</script>

<style>

</style>