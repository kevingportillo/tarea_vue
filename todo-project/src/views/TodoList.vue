<template>
    <div>
    <h1>Todoリスト</h1>
    <!-- @submit.preventを追加 -->
    <form @submit.prevent="addTodo()">
    <!-- v-modelを追加 -->
    <input v-model="todo">
    </form>
    <el-row :gutter="12">
    <el-col :span="12"  v-for="( todo, index ) in todos" :key="index">
        <el-card class="box-card" shadow="hover" style="margin: 5px 0;">
        <el-row :gutter="12">
            <el-col :span="21">{{ todo }}</el-col>
            <el-col :span="3">
            <el-button @click="removeTodo(index)" type="success" icon="el-icon-check" circle></el-button>
            </el-col>
        </el-row>
        </el-card>
    </el-col>
    </el-row>
    </div>
</template>

<script>
export default {
    name: 'TodoList',
      // dataプロパティを追加
data() {
    return {
    todo: '',
          // todosプロパティを追加
    todos: [],
    }
},
  // methodsプロパティを追加
methods: {
    addTodo(){
      this.todos.push(this.todo); //--1
      this.todo = ''; //--2
    },
    // todoを削除するメソッドを作成
    removeTodo(index){ 
      this.todos.splice(index, 1); //--1
    }
}
}
</script>