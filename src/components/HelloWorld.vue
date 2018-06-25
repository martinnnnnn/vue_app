<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <Component1/>
    <Component1
      v-for="item in groceryList"
      v-bind:todo="item"
      v-bind:key="item.id">
    </Component1>
    <input type="text" v-model="newItem">
    <p> {{newItem}} </p>
    <button v-on:click="AddToList">Add item</button>
    <button v-on:click="ConnectToServer">Connect</button>
    <h2>Essential Links</h2>
    <ul>
      <li>
        <a
          href="https://vuejs.org"
          target="_blank"
        >
          Core Docs
        </a>
      </li>
      <li>
        <a
          href="https://forum.vuejs.org"
          target="_blank"
        >
          Forum
        </a>
      </li>
      <li>
        <a
          href="https://chat.vuejs.org"
          target="_blank"
        >
          Community Chat
        </a>
      </li>
      <li>
        <a
          href="https://twitter.com/vuejs"
          target="_blank"
        >
          Twitter
        </a>
      </li>
      <br>
      <li>
        <a
          href="http://vuejs-templates.github.io/webpack/"
          target="_blank"
        >
          Docs for This Template
        </a>
      </li>
    </ul>
    <h2>Ecosystem</h2>
    <ul>
      <li>
        <a
          href="http://router.vuejs.org/"
          target="_blank"
        >
          vue-router
        </a>
      </li>
      <li>
        <a
          href="http://vuex.vuejs.org/"
          target="_blank"
        >
          vuex
        </a>
      </li>
      <li>
        <a
          href="http://vue-loader.vuejs.org/"
          target="_blank"
        >
          vue-loader
        </a>
      </li>
      <li>
        <a
          href="https://github.com/vuejs/awesome-vue"
          target="_blank"
        >
          awesome-vue
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
import Component1 from './Component1'

export default {
  name: 'HelloWorld',
    components: {
    Component1
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      groceryList:
      [
        { id: 0, text: 'Vegetables' },
        { id: 1, text: 'Cheese' },
        { id: 2, text: 'Whatever else humans are supposed to eat' }
      ],
      newItem:''
    }
  },

  methods: {
    AddToList: function (event) {
      this.groceryList.push({ text:this.newItem })
    },
    ConnectToServer: function(event) {
      var socket = io.connect('http://localhost:3000');
      socket.on('message', function(message) {
          alert('Le serveur a un message pour vous : ' + message);
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
