<template>
  <div>
    <header><h1>ToDo's</h1></header>
    <section id="form-section">
      <form v-on:submit.prevent="saveNewItem">
        <input type="text" id="new-item" placeholder="Enter new item" v-model="newItem">

        <label for="new-item">High</label>
        <input type="radio" name="priority" id="new-item" value="true" v-model="newPriority">

        <label for="new-item">Low</label>
        <input type="radio" name="priority" id="new-item" v-model="newPriority">

        <button type="submit">Save Item</button>
      </form>
    </section>
    <section id="list-section">
      <ul>
        <li v-for="(item, index) in items" :key="index" :class="item.priority ? 'high' : 'low' " >
          <p>{{item.item}} is {{item.priority}}</p>
          <!-- <p>v-if="item.priority"
          </p> -->
        </li>
      </ul>
    </section>
  </div>
</template>

<script>
  export default {
    data(){
      return {
        items: [],
        newItem: "",
        newPriority: ""
      }
      
    }, 
    methods:{
      saveNewItem: function(){
        this.items.push({
          item: this.newItem,
          priority: this.newPriority
        })
        this.newItem = "", 
        this.newPriority = ""
      }
      
    }
  }
</script>

<style>

h1{
  display: grid;
  justify-content: center;
}



li.high{ 
  background-color: red;
  list-style-type: none;
}

li.low{
  background-color: lime;
  list-style-type: none;

}

</style>