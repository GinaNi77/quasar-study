<template>

  <q-page class="flex flex-center">
   <q-card class="my-card bg-pink-1" style="width: 600px">
      <q-card-section>
       <div class="text-h4 text-weight-bol text-pink-10 text-center">My Todo List</div>
      </q-card-section>

       <div class="row justify-center">
            <div class="q-pb-md " v-if="editing">
              <q-btn round dense flat icon="close" @click="doEdit(false)" color="pink-8"/>
            </div>
            <div class="q-pb-md " v-else>
              <q-btn round dense flat icon="edit" @click="doEdit(true)" color="pink-8"/>
            </div>
        </div>

      <q-card-section v-if:="editing">
        <div class="row justify-center">
          <div class="col-10">
           <q-input outlined v-model="newTodo" label="add todo">
            <template v-slot:after>
              <q-btn round dense flat icon="send" class="text-pink-10" @click="addTodo" :disabled="newTodo===''"/>
            </template>
           </q-input>
          </div>
        </div>
      </q-card-section>

      <q-card-section v-if="todoList.length>0">
        <div class="row justify-center" v-for="todo in todoList" :key="todo.id" @click="todo.done=!todo.done">
          <div class="col-auto q-mr-sm q-pb-md">
            <q-checkbox v-model="todo.done" color="pink-10"/>
          </div>
          <div class="col-8 items-center flex q-pb-md" :class="{'text-pink-10' : todo.done}">
            {{todo.value}}
          </div>
          <div class="col-auto q-pb-md">
            <q-btn round dense flat icon="delete" @click="deleteTodo(index)" color="pink-8"/>
          </div>
        </div>
      </q-card-section>

      <q-card-section v-else>
        <div class="row justify-center text-h6 ">
          No todos
        </div>
      </q-card-section>
      

    </q-card>
  </q-page>
</template>

<script>
import {defineComponent} from 'vue'

export default defineComponent({
  name: 'IndexPage',
  data(){
    return{
      editing: false,
      newTodo:"",
      todoList: [
        {id:"1", value: "buy apples", done: false},
        {id:"2", value: "buy bananas", done: false},
        {id:"3", value: "buy cherry", done: false}
      ]    
      }
  },
  methods: {
    addTodo(){
      this.todoList.push({id: this.todoList.length+1, value: this.newTodo, done:false })
      this.newTodo=""
    },
    deleteTodo(index){
      this.todoList.splice(index, 1)
    }, 

    doEdit(e){
    this.editing = e
    this.newTodo = ""
    }
  }
})
</script>
