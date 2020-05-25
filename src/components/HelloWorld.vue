<template>
  <div class="hello">
    <input type="checkbox" v-model='dynamically_added.stored_value'>
    <input type="text" v-model='dynamically_added.stored_text' v-on:keyup.enter="adding_object">
    <button v-on:click="remove_all">Clear List</button>

    <li v-for="(values,index) in stored_data" v-bind:key="values">
      <input type="checkbox">
      <span> {{values.stored_text}} </span>
      <button v-on:click="remove_one(index)">X</button>
    </li>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data:function() {
    return {
      stored_data: [
        {
          stored_text: 'Sample Text',
          stored_value: true
        },
        {
          stored_text: 'Sample Text2',
          stored_value: true
        }
      ],
      dynamically_added: {
        stored_text: '',
        stored_value: ''
      }
    }
  },
  methods: {
    adding_object: function() {
      this.stored_data.unshift({
        stored_text: this.dynamically_added.stored_text,
        stored_value: this.dynamically_added.stored_value
      }),
      this.dynamically_added.stored_text = '',
      this.dynamically_added.stored_value = ''
    },
    remove_one: function(current_index) {
      this.stored_data.splice(current_index, 1);
    },
    remove_all: function() {
      this.stored_data.splice(0, this.stored_data.length);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
