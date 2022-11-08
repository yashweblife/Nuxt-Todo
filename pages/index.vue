<template>
  <main>
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
    <div class="content">
      <ul>
        <li>
          <h2>Title</h2>
          <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Molestias laudantium praesentium animi dolor
            corporis amet sequi quisquam veniam dolorum rerum, impedit modi! Suscipit eos ex beatae nulla dicta quae
            consectetur?
          </p>
          <nav>
            <button>Open</button>
            <button>Delete</button>
          </nav>
        </li>
        <li>
          <h2>Title</h2>
          <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Molestias laudantium praesentium animi dolor
            corporis amet sequi quisquam veniam dolorum rerum, impedit modi! Suscipit eos ex beatae nulla dicta quae
            consectetur?
          </p>
          <nav>
            <button>Open</button>
            <button>Delete</button>
          </nav>
        </li>
      </ul>
      <button @click="openAlert">Make a New List</button>
    </div>
    <AlertBox title="Add something" :trigger="open_alert" :inputs="[{id:0, name:'test'},{id:1,name:'title'}]" @alert-box-completed="handleAlert"/>
  </main>
</template>

<script lang="ts">
import Vue from 'vue'
import { ItemInterface } from '~/interfaces'
import AlertBox from '~/components/AlertBox.vue'
export default Vue.extend({
  name: 'IndexPage',
  components:{
    AlertBox
  },
  data: () => {
    const lists: ItemInterface[] = []
    return ({
      lists,
      alert_open: false,
      open_alert:false,
    })
  },
  methods:{
    handleAlert(a:any){
      console.log(a)
      this.open_alert = false
    },
    openAlert(){
      this.open_alert = true
    }
  }
})
</script>


<style lang="scss" scoped>
* {
  font-family: Arial, Helvetica, sans-serif;
}

header {
  display: flex;
  align-items: center;
  justify-content: space-between;

  >.text {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    width: 100%;

    h1 {
      padding: 0;
      margin: 0;
    }

    p {
      padding: 0;
      margin: 0;
      color: rgb(26, 187, 171);
    }
  }

  nav {
    width: 100%;
    display: flex;
    align-items: center;

    >a {
      width: 50%;
      text-decoration: none;
      cursor: pointer;
      color: black;
      transition:0.2s color;
      &:hover{
        color:rgb(26, 187, 171);
      }
    }
  }
}


</style>