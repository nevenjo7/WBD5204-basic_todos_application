<template>
  <div class="hello">
    <div class="sample">
    <input type="checkbox" v-model='dynamically_added.stored_value'>
    <input type="text" v-model='dynamically_added.stored_text' v-on:keyup.enter="adding_object" v-bind:placeholder="placeholder">
    <button v-on:click="remove_all">Clear List</button>
    <div class="clear"></div>
    </div>
    <li v-for="(values,index) in stored_data" v-bind:key="values">
      <div class="sample">
      <input type="checkbox">
      <span> {{values.stored_text}} </span>
      <button v-on:click="remove_one(index)">X</button>
      <div class="clear"></div>
      </div>
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
          stored_text: 'This is an example task. Delete or add your own',
          stored_value: true
        },
        {
          stored_text: 'Learn Vue JS',
          stored_value: true
        },
        {
          stored_text: 'Learn Javascript',
          stored_value: true
        },
        {
          stored_text: 'Create Presentation for diff between ES6 and JS',
          stored_value: true
        }

      ],
      dynamically_added: {
        stored_text: '',
        stored_value: ''
      },
      placeholder: 'What do you need to do?'
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
button {
  background-color: #fff;
  padding: 5px 15px;
  outline: none;
  color: #585858;
  border: 1px solid #BBBBBB;
}
li .sample {
  background-color: #3564A4;
}
.sample {
  background-color: #E7E8EB;
  padding: 20px 10px;
  
  input[type='text'] {
    width: 70%;
    padding: 5px 5px;
    float: left;
    margin-left: 40px;
  }
  input[type='text']:focus {
    outline: 2px solid #81B7F6;
  }
  input[type='checkbox'] {
    float: left;
    margin: 8px 0px;
  }
  button {
    float: right;
    margin: 5px 0px;
  }
  span {
    float: left;
    color: #fff;
    margin: 5px 40px;
  }
  .clear {
    clear: both;
  }
  
  
}
li {
  list-style-type: none;
  border: 1px solid #fff;
}
</style>
