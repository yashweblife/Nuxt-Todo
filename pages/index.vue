<template>
  <header>
    <div class="text">
      <h1>Awesom Nuxt TodoList App</h1>
      <p>I made this to learn nuxt and vue so its buggy</p>
    </div>
    <nav>
      <a href="/lists">
        <h3>Lists</h3>
      </a>
      <a href="/settings">
        <h3>Settings</h3>
      </a>
      <a href="/projects">
        <h3>Projects</h3>
      </a>
    </nav>
  </header>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'IndexPage'
})
</script>


<style lang="scss" scoped>
  header{
    display: flex;
    align-items: center;
    justify-content: space-between;
    font-family: Arial, Helvetica, sans-serif;
    >.text{
      display: flex;
      flex-direction: column;
      align-items: flex-start;
      width: 100%;
      h1{
        padding:0;
        margin:0;
      }
      p{
        padding:0;
        margin:0;
        color:rgb(26, 187, 171);
      }
    }
    nav{
      width:100%;
      display: flex;
      align-items: center;
      >a{
        width:50%;
        text-decoration: none;
        cursor: pointer;
        color:black;
      }
    }
  }
</style>