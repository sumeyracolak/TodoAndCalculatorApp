<template>
  <main>
    <header>
        <h1>TODO</h1>
        <DocumentationIcon />
    </header>
    <NewToDo @add="addItem"/>
    <div v-if="items.length === 0" style="margin-bottom:10px;">No items</div>
    <div v-else>
      <div class="todo-body">
          <ToDoItem :item="item" v-for="(item, index) in filteredItems" :key="index"/>
      </div>
    </div>
    <ToDoFilters 
      :leftItems="leftItems"
      @showAllItems="showAllItems" 
      @showActiveItems="showActiveItems"
      @showCompleatedItems="showCompleatedItems" 
      @removeCompleatedItems="removeCompleatedItems" 
    />
  </main>
</template>
<script>
  import DocumentationIcon from '../components/icons/IconDocumentation.vue'
  import NewToDo from '../components/ToDoApp/NewToDo.vue'
  import ToDoItem from '../components/ToDoApp/ToDoItem.vue'
  import ToDoFilters from '../components/ToDoApp/ToDoFilters.vue'
  export default{
    components:{DocumentationIcon,NewToDo,ToDoItem,ToDoFilters},
    data(){
      return{
        items: [],
        showCompleated: false,
        showActive: false
      }
    },
    methods:{
      addItem(newItem){
        this.items.push({text: newItem, compleated: false})
      },
      showAllItems() {
        this.showCompleated = false;
        this.showActive = false;
      },
      showActiveItems(){
        this.showCompleated = false;
        this.showActive = true;
      },
      showCompleatedItems() {
        this.showCompleated = true;
        this.showActive = false;
      },
      removeCompleatedItems() {
        this.items = this.items.filter(item => !item.compleated);
      }
    },
    computed: {
      filteredItems() {
        if (this.showCompleated) {
          return this.items.filter(item => item.compleated);
        }
        else if (this.showActive) {
          return this.items.filter(item => !item.compleated);
        }
        else {
          return this.items;
        }
      },
      leftItems(){
        return (this.items.filter(item => !item.compleated).length);
      }
    }
  }
</script>
<style scoped>
  main{width:500px;margin:auto;}
  header{float:left;width:100%;display:flex;align-items:center;justify-content:space-between;}
  .todo-body{float:left;width:100%;background:#333;}
</style>