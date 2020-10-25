<template>
  <div id="app" style="display: flex; padding: 0 5% 0 0;">
    <div id="d1" style="height: 100vh; background-color: alice">
      <h3 style="margin: 25% 0;">Toolbox</h3>
        <draggable class="list-group" :list="list1" group="people" @change="log">
          <div
            class="list-group-item"
            v-for="(element, index) in list1"
            :key="index"
            style="padding: 5%; margin: 6% 0;"
          >

            <div 
              class="input-wrapper" 
              v-if="element.type === 'input'"
              style="
                display: flex;
                flex-direction: column;
                border: 1px dashed;
                padding: 2%;
              "
            >
              <label for="input" style="align-self: start;">Input text:</label>
              <input id="input" type="text" style="border-style: inset;"/>

            </div>
            
            <div class="select-wrapper" v-if="element.type === 'checkbox'"
              style="
                display: flex;
                flex-direction: column;
                align-items: center;
              "
            >
              <label for="options">Selecione uma opção:</label>
              <select id="options">
                <option value="1"> 1 </option>
              </select>
            </div>

            <button v-if="element.type === 'button'"> button </button>
          </div> 
        </draggable>
    </div>

      <hr>
      <div id="d2" style="padding: 0 4%;">
        <h3 style="margin: 15% 0;">Insira aqui de acordo com sua escolha</h3>
        <draggable class="list-group" :list="list2" group="people" @change="log">
          <div
            class="list-group-item"
            v-for="(element, index) in list2"
            :key="index"
            style="padding: 5%; margin: 2% 0;"
          >
            <div 
              class="input-wrapper" 
              v-if="element.type === 'input'"
              style="
                display: flex;
                flex-direction: column;
                border: 1px dashed;
                padding: 2%;
              "
            >
              <label for="input" style="align-self: start;">Input text:</label>
              <input id="input" type="text" style="border-style: inset;"/>

            </div>
            
            <div class="select-wrapper" v-if="element.type === 'checkbox'">
              <label for="options">Selecione uma opção:</label>
              <select id="options">
                <option value="1"> 1 </option>
              </select>
            </div>

            <button v-if="element.type === 'button'"> button </button>
          </div> 
        </draggable>
      </div>
  </div>
</template>

<script>
import draggable from "@/vuedraggable"
export default {
  name: "two-lists",
  display: "Two Lists",
  order: 1,
  components: {
    draggable
  },
  data() {
    return {
      list1: [
        { type: "input", id: 1 },
        { type: "checkbox", id: 2 },
        { type: "button", id: 3 },
      ],
      list2: [
        // { name: "Juan", id: 5 },
        // { name: "Edgard", id: 6 },
        // { name: "Johnson", id: 7 }
      ]
    };
  },
  methods: {
    add: function() {
      this.list.push({ name: "Juan" });
    },
    replace: function() {
      this.list = [{ name: "Edgard" }];
    },
    clone: function(el) {
      return {
        name: el.name + " cloned"
      };
    },
    log: function(evt) {
      window.console.log(evt);
    }
  }
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}

button, input, select, textarea {
  border-style: inset;
}
</style>
