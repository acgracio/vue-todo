<template>
  <div class="todoListContainer">
    <div class="heading">
      <div class="text-3xl font-semibold text-center	">Todo List</div>
      <div><add-item-form /></div>
      
    </div>
    <list-view :items="items" v-on:reloadlist="getList()" />
  </div>
</template>

<script>
import addItemForm from "./addItemForm";
import listView from "./listView";

export default {
  components: {
    addItemForm,
    listView,
  },
  data: function () {
    return {
      items: [],
    };
  },
  methods: {
    getList() {
      axios
        .get("api/items")
        .then((response) => {
          this.items = response.data;
        })
        .catch((erro) => {
          console.log(error);
        });
    },
  },
  created() {
    this.getList();
  },
};
</script>

<style scoped>
.todoListContainer {
  width: 350px;
  margin: auto;
}

.heading {
  background: #e6e6e6;
  padding: 10px;
}

#title {
  text-align: center;
}
</style>