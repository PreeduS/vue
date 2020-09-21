<template>
  <div>
    <div v-bind:title = "hoverMessage">counter: {{counter}}</div>
    <br />
    <button v-on:click = "increment">Increment</button>
    <br />
    Two  way binding: <input  v-model = "message" />  {{message}}
    <br />
    <button v-on:click = "toggleVisible">Increment</button> <span v-if = "visible">visible</span>
    <br />
    <div v-for="todo in todos" v-bind:key = "todo.id">
      {{todo.label}}
    </div>
    <Item 
      v-for="todo in todos" 
      v-bind:key = "todo.id" 
      v-bind:label = "todo.label" 
      v-bind:active = "todo.active" 
      v-bind:id = "todo.id"
      v-on:toggle-active= "toggleActive"
      v-on:delete-item= "deleteItem"
      >
      
    </Item>
  </div>
</template>


<script>
import Item from './Item.vue'


export default {
  name: 'Introduction',
  data:() => {
      return {
        counter: 0,
        hoverMessage: 'tooltip',
        message: 'initial value',
        visible: true,
        todos:[
            {id: 1, label: 'a', active: true},
            {id: 2, label: 'b', active: false},
        ]
      }
  },
  /*mounted(){
    setInterval(() => {
      this.counter++
    }, 1000)
  }*/
  methods:{
      increment(){
          this.counter++
      },
      toggleVisible(){
          this.visible = !this.visible
      },
      toggleActive(id){
        const todo = this.todos.find(x => x.id === id);
        if(todo !== undefined){
          todo.active = !todo.active
        }

      },
      deleteItem(id){
        this.todos = this.todos.filter(x => x.id !== id)

      }
  },
  components: {
    Item
  }
}

/*
Directives are prefixed with v-
*/


</script>


