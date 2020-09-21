<template>
  <div>
    <div v-bind:class="{'is-active':active}">
        label: {{label}}
    </div>
    <input type="checkbox" v-on:change = "toggleActive" /> 
    <button @click = "$emit('toggle-active', id)">Toggle</button>
    <button @click = "$emit('delete-item', id)">Delete</button>
  </div>
</template>


<script>
export default {
  name: 'Item',
  methods:{
    toggleActive(){
      //this.active = !this.active;
    }
  },
  props: {
    id: Number,
    label: String,
    active: Boolean,
  }
  // props: ['label']
}
</script>

<style scoped>
.is-active {
  font-weight: bold;
}
</style>>