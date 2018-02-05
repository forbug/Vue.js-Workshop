<template>
  <div class="row">
    <div class="col-lg-12">

      <h1>WELCOME</h1>

      <p class="subtitle">
        Built with Vue.js, Bootstrap, and FontAwesome
        <i class="fa fa-thumbs-up"></i>
      </p>

      <!-- RENDER DATA -->
      <p class='lead'>{{ msg }}</p>

      <!-- DIRECTIVES -->
      <!-- V-MODEL DIRECTIVE INPUT-->
      <input type='text' class="form-control" v-model="msg" />

      <!-- HANDLEBARS EXPRESSION -->
      <p>
        {{ checked ? 'Go' : 'Stop' }}
      </p>

      <!-- V-MODEL DIRECTIVE CHECKBOX -->
      <input type="checkbox" v-model="checked">

      <!-- V-IF DIRECTIVE -->
      <i class='fa fa-check' v-if="checked"></i>

      <!-- V-IF + expression -->
      <i class='fa fa-check' v-if="checked"></i>
      <i class='fa fa-times' v-if="!checked"></i>

      <!-- V-ELSE DIRECTIVE -->
      <!-- V-ELSE-IF is also allowed -->
      <i class='fa fa-check' v-if="checked"></i>
      <i class='fa fa-times' v-else></i>

      <!-- V-BIND DIRECTIVE -->
      <i v-bind:class="checked ? 'fa fa-check' : 'fa fa-times'"></i>

      <!-- Simplified above with a 'computed' component property -->
      <i v-bind:class="checkedIcon"></i>

      <br>

      <!-- V-ON DIRECTIVE -->
      <!-- Great for triggering an action that mutates the component's data -->
      <!-- rather than having this element `MODEL` the data, like the v-model directive -->
      <button class="btn btn-dark" v-on:click="checked = !checked">
        <!-- STEP 1 -->
        <i v-bind:class="checked ? 'fa fa-check' : 'fa fa-times'"></i>
        <!-- STEP 2 -->
        {{ checked ? 'Checked' : 'Unchecked' }}
      </button>

      <!-- REVIEW -->
      <!-- QUESTIONS / TAKE 5 -->

      <!-- V-FOR DIRECIVE - ITERATION -->
      <ul class='list-group'>
        <li class='list-group-item' v-for="each in todos" v-bind:key="each.label">

          <!-- STEP 2 nested if -->
          <!-- <i class='fa fa-check' v-if="each.done"></i> -->
          <!-- <i class='fa fa-square-o' v-else></i> -->

          <!-- STEP 2 - MORE ADVANCED -->
          <!-- INTRODUCE COMPUTED SINCE THIS IS REPEATED LOGIC -->
          <i v-bind:class="each.done ? 'fa fa-check' : 'fa fa-times'" v-on:click="each.done = !each.done"></i>

          <!-- STEP 1 nested text -->
          {{ each.label }}

          <!-- STEP 3 - nested v-model -->
          <input type="checkbox" v-model="each.done">

        </li>
      </ul>

      <br>

      <!-- LETS ADD AN INPUT AND BUTTON TO CREATE A NEW TODO -->
      <!-- STEP 1 - ADD newTodo: to this.data -->
      <div class="card card-body">
        <label>New Todo</label>
        <input type='text' class="form-control" v-model="newTodo"/>
        <br>
        <button class="btn btn-success" @click="addTodo">
          <i class="fa fa-check"></i>
          Add
        </button>
      </div>

      <!-- REVIEW -->
      <!-- We learned about the V-FOR DIRECTIVE -->
      <!-- Used the v-model directive in conjunction with a v-on:click directive -->
      <!-- to add a new TODO to the list -->

      <!-- QUESTIONS -->

      <!-- LET'S ADD A FUNCTION TO REMOVE A TODO -->
      <!-- WIRE IT UP TO V-ON:CLICK DIRECIVE -->
      <ul class='list-group'>
        <li class='list-group-item' v-for="each in todos" v-bind:key="each.label">

          <!-- STEP 2 nested if -->
          <i class='fa fa-check' v-if="each.done"></i>
          <i class='fa fa-square-o' v-else></i>

          <!-- STEP 1 nested text -->
          {{ each.label }}

          <!-- STEP 3 - nested v-model -->
          <input type="checkbox" v-model="each.done">

          <!-- STEP 4 - INVOKE METHODS -->
          <button class="btn btn-sm btn-danger pull-right" v-on:click="trashTodo(each)">
            <i class="fa fa-trash"></i>
          </button>

        </li>
      </ul>

      <!-- WHAT'S NEXT -->
      <!-- Adding more routes -->
      <!-- Interfacing with APIs -->
      <!-- Complex State Management -->
      <!-- Advanced features - mixins, custom directives, slots, filters, server-side rendering -->

    </div>
  </div>
</template>

<!-- // // // // -->

<script>

export default {
  name: 'Hello',
  data () {
    return {
      msg: 'Welcome to Vue Workshop!',
      checked: true,
      newTodo: '',
      todos: [
        { label: 'Study', done: true, editing: '' },
        { label: 'Sleep', done: false, editing: '' },
        { label: 'Eat', done: true, editing: '' },
        { label: 'Code', done: true, editing: '' }
      ]
    }
  },
  methods: {
    trashTodo (todo) {
      this.todos = this.todos.filter(e => { return e.label !== todo.label })
    },
    addTodo () {
      this.todos.push({ label: this.newTodo, done: false, editing: '' })
      this.newTodo = ''
    }
  },
  computed: {
    checkedIcon () {
      return checked ? 'fa fa-check' : 'fa fa-times'
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
