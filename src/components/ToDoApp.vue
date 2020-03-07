<template>
  <div id="appcontainer">
    <input 
    type="text" 
    placeholder="todo"
    class="input" 
    v-model="newItem">
    <button class="button" @click="addItem">Dodaj</button>
    <div v-if="this.elem === 1" class="info">Nie masz żadnych zadań</div>
    <ToDoItem
      v-for="item in items"
      v-bind:key="item.id"
      v-bind:item="item"
      @removeClicked="removeItem"
    />
  </div>
</template>

<script>
import ToDoItem from "./ToDoItem.vue";
export default {
  components: {
    ToDoItem
  },
  data() {
    return {
      newItem: "",
      items: [
      ],
      elem: 1
    };
  },
  methods: {
    addItem() {
      var check = this.newItem.trim();
      if (check === "") {
        alert("Pole nie może być puste!");
      } else {
        this.items.push({
          id: this.items.length + 1,
          title: this.newItem,
          completed: false
        });
        this.newItem = "";
        this.elem = 0;
      }
    },
    removeItem(id) {
      const index = this.items.findIndex(el => el.id === id);
      this.items[index].completed = true;
    }
  }
};
</script>

<style>

.appcontainer {
    width: 100%;
}
.input {
    width: 250px;
    margin: 10px 0;
    padding: 0 10px;
    border: none;
    border-bottom: 2px solid #238161;
    font-size: 16px;
}

.button {
    width: 150px;
    margin: 10px;
    padding: 10px;
    border: none;
    border-radius: 25px;
    background-color: #238161;
    color: #fff;
    cursor: pointer;
}

.info {
    margin: 50px 0;
    text-align: center;
}

.item {
  max-width: 80%;
  border: 1px solid #cdcdcd;
  margin: 9px;
  padding: 10px;
  text-align: center;
}
.item h2 {
  transition: 0.5s ease all;
}
.completed {
  opacity: 0.5;
}
.completed h2 {
  text-decoration: line-through;
  color: red;
}
</style>


