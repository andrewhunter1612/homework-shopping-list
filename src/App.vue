<template>
  <div>
    <header><h1>ToDo's</h1></header>
    <section id="form-section">
      <form v-on:submit.prevent="saveNewItem">
        <input type="text" id="new-item" placeholder="Enter new item">

        <label for="new-item">High</label>
        <input type="radio" name="priority" id="new-item" value="high">

        <label for="new-item">Low</label>
        <input type="radio" name="priority" id="new-item" value="low">

        <button type="submit">Save Item</button>
      </form>
    </section>
    <section id="list-section">
      <ul>
        <li v-for="(item, index) in items" :key="index" :class="list-item">
          <p>{{item.item}} is {{item.priority}} priority</p>
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
        newItem: {},
        newPriority: ""
      }
      
    }, 
    methods:{
      saveNewItem: function(){
        this.items.push({
          item: this.newItem,
          priority: this.priority
        })
      }
      
    }
  }
</script>

<style lang="scss" scoped>

</style>