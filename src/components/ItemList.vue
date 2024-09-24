<template>
    <div>
      <h1>Item List </h1>
      <form @submit.prevent="addItem">
        <input v-model="newItem" placeholder="Add new item" />
        <button type="submit">Add</button>
      </form>
      <ul>
        <li v-for="(item, index) in items" :key="index">
          {{ item }}
          <button @click="editItem(index)">Edit</button>
          <button @click="deleteItem(index)">Delete</button>
        </li>
      </ul>
  
      <div v-if="isEditing">
        <input v-model="editedItem" />
        <button @click="updateItem">Update</button>
        <button @click="cancelEdit">Cancel</button>
      </div>
    </div>
  </template>
  
  <script>
  import { ref } from 'vue';
  
  export default {
    setup() {
      const items = ref(['Learn Vue Composition API', 'Build a CRUD App']);
      const newItem = ref('');
      const isEditing = ref(false);
      const editedIndex = ref(null);
      const editedItem = ref('');
  
      const addItem = () => {
        if (newItem.value) {
          items.value.push(newItem.value);
          newItem.value = '';
        }
      };
  
      const deleteItem = (index) => {
        todos.value.splice(index, 1);
      };
  
      const editItem = (index) => {
        editedIndex.value = index;
        editedItem.value = items.value[index];
        isEditing.value = true;
      };
  
      const updateItem = () => {
        if (editedItem.value) {
          items.value.splice(editedIndex.value, 1, editedItem.value);
          isEditing.value = false;
          editedItem.value = '';
        }
      };
  
      const cancelEdit = () => {
        isEditing.value = false;
        editedItem.value = '';
      };
  
      return {
        items,
        newItem,
        isEditing,
        editedItem,
        addItem,
        deleteItem,
        editItem,
        updateItem,
        cancelEdit,
      };
    },
  };
  </script>
  
  <style scoped>
  h1 {
    color: #42b983;
  }
  </style>
  