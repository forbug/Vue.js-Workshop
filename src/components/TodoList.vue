<template>
  <div class="row">
    <div class="col-lg-12">

      <!-- Interpolte between HTML tags -->
      <p class="lead">
        {{ message }}
      </p>

      <!-- Interpolate expressions -->
      {{ checked ? 'Go' : 'Stop' }}

      <!-- `v-model` directive - binds this.message -->
      <input type="text" class='form-control' v-model="message">

      <!-- `v-model` directive - binds this.checked in JS-->
      <input type="checkbox" v-model="checked">

      <!-- `v-if` directive -->
      <i class="fa fa-check" v-if="checked"></i>
      <i class="fa fa-times" v-else></i>

      <div class="card card-body">

        <div class="row">
          <div class="col-lg-12">
            <!-- `v-bind:some_attribute` directive -->
            <!-- Evaluates some JS and assigns it to an attribute on an HTML element -->
            <i v-bind:class=" checked ? 'fa fa-check' : 'fa fa-times' "></i>

            <!-- `v-on:some_event` directive -->
            <!-- Assigns an event handler method to an HTML element  -->
            <button class="btn btn-dark" v-on:click="onClick('ON')">ON</button>
            <button class="btn btn-dark" v-on:click="onClick('OFF')">OFF</button>
          </div>
        </div>

      </div>

      <hr>

      <div class="row">

        <!-- V-FOR -->
        <div class="col-lg-6">
          <ul class="list-group">
            <li :class='eachCss(each)' v-for="each in todos" :key="each.label">

              <!-- todoIcon computed -->
              <i v-bind:class="eachIcon(each)" v-on:click="each.done = !each.done"></i>

              {{ each.label }}

              <button class="btn btn-danger pull-right btn-sm" @click="removeTodo(each)">
                <i class="fa fa-trash"></i>
              </button>

            </li>
          </ul>
        </div>

        <div class="col-lg-6">
          <Form v-bind:addTodo="add"/>
        </div>

      </div>

      <p class="subtitle">
        Built with Vue.js, Bootstrap, and FontAwesome
        <i class="fa fa-thumbs-up"></i>
      </p>

    </div>
  </div>
</template>

<!-- // // // // -->

<script>

import Form from './Form'

export default {
  name: 'Hello',
  components: {
    Form
  },
  data () {
    return {
      message: 'Welcome to Vue workshop',
      checked: true,
      todos: [
        { label: 'Sleep', done: true },
        { label: 'Eat', done: false }
      ]
    }
  },
  methods: {
    onClick (message) {
      this.checked = !this.checked
      this.message = message
    },
    add (newTodo) {
      this.todos.push({ label: newTodo, done: false })
      this.newTodo = ''
    },
    removeTodo (todo) {
      this.todos = this.todos.filter(e => { return e.label !== todo.label })
    },
    eachCss (each) {
      return each.done ? 'list-group-item list-group-item-success' : 'list-group-item'
    },
    eachIcon (each) {
      return each.done ? 'fa fa-check' : 'fa fa-square-o'
    }
  }
}

</script>

<!-- // // // // -->

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  p.subtitle {
    font-size: 1.25rem;
    color: #999999;
  }
</style>
