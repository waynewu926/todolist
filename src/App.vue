<template>
  <div class="box">
    <div class="title">Todo-List</div>

    <div class="addBox">
      <input v-model="content" class="addContent" type="text" placeholder="Add a todo">
      <div @click="add" class="addButton">add todo</div>
    </div>

    <div v-for="(item, index) in items" :key="index" :class="[item.isCompleted ? 'completed' : 'item']">
      <div>
        <input v-model="item.isCompleted" type="checkbox">
        <span class="name">{{ item.task }}</span>
      </div>
      <div @click="del(index)" class="delete">delete</div>
    </div>

  </div>
</template>

<script setup>
import { ref } from 'vue';


const content = ref('');

const items = ref([
  {
    isCompleted: false,
    task: 'have lunch'
  },
    {
    isCompleted: false,
    task: 'exercise' 
  },
  {
    isCompleted: false,
    task: 'study'
  }
])

function add() {
  if (content.value != '') {
    items.value.push({
      isCompleted: false,
      task: content.value
    });
  
    content.value = '';
  }
}

function del(index) {
  items.value.splice(index, 1);
}

</script>

<style>
 body {
      background: linear-gradient(to right,
          rgb(113, 65, 168),
          rgba(44, 114, 251, 1));
    }

    .box {
      width: 65%;
      height: 570px;
      background-color: #ffff;
      border-radius: 20px;
      margin: 90px auto;
      padding-top: 30px;
    }

    .title {
      font-size: 30px;
      font-weight: bold;
      text-align: center;
      user-select: none;
    }

    .addBox {
      display: flex;
      margin-top: 30px;
      margin-bottom: 30px;
      margin-left: 100px;
    }

    .addContent {
      border: 1px solid #dfe1e5;
      outline: none;
      width: 60%;
      height: 45px;
      border-radius: 20px 0 0 20px;
      padding-left: 15px;
    }

    .addButton {
      width: 100px;
      height: 49px;
      border-radius: 0 20px 20px 0;
      text-align: center;
      line-height: 49px;
      color: #ffff;
      cursor: pointer;
      user-select: none;
      background: linear-gradient(to right,
          rgb(113, 65, 168),
          rgba(44, 114, 251, 1));
    }

    .item {
      display: flex;
      box-sizing: border-box;
      width: 70%;
      height: 50px;
      margin: 8px auto;
      padding: 16px;
      border-radius: 20px;
      box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 20px;
      align-items: center;
      justify-content: space-between;
    }

    .name {
      user-select: none;
    }

    .delete {
      color: red;
      user-select: none;
    }

    .completed {
      display: flex;
      box-sizing: border-box;
      width: 70%;
      height: 50px;
      margin: 8px auto;
      padding: 16px;
      border-radius: 20px;
      box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 20px;
      align-items: center;
      justify-content: space-between;
      text-decoration: line-through;
      opacity: 40%;
    }
</style>
