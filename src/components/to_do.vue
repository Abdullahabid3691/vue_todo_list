<template>
    
<div>
 <input type="text" id="new_todo" v-model='new_todo' @keyup.enter="add_todo">
 <br><br>
 <button @click='add_todo'>Add Todo</button>
 <span v-show='todo_exists'>   Already exists ! </span>
 <h3>ToDo List</h3>
 <h5 v-if='todo_number==0'>No item in todo list</h5>
  <ul>
    <li v-for='todo in todo_list' >
      {{todo.title}}    <button @click="remove_todo(todo.id)" v-bind:value="todo.id">Remove</button>   <button @click="update_todo(todo.id)" v-bind:value="todo.id">Update</button>  
      <!-- <router-link tag="button" @click="update_todo(todo.id)" v-bind:value="todo.id" to='/'>Update</router-link>  -->
    </li>
  </ul>
</div>
</template>


<script>
import { METHODS } from 'http';
export default {
    // name:'app'
    data(){
        return {
            new_todo: '',
            todo_list: [],
            todo_link: '',
            todo_number:0,
            todo_exists:false
        }
    },

    methods:{
        add_todo:function(){
            var already_in_list = this.todo_list.includes(this.new_todo)
            if(!already_in_list){
                /* link_text = '<a href="'+id+'">Remove</a>' */
                /* + ' ' + link_text */
                this.todo_id =  this.todo_list.length
                var new_todo_obj = {'title':this.new_todo,'id':this.todo_id}
                
                this.todo_list.push(new_todo_obj);
                this.todo_number++;
                this.todo_exists = false
                }
                else{
                    this.todo_exists = true
                    console.log('Already exists')
                }
        },
      remove_todo: function(id){
        if(confirm("remove this todo?"+id)){
          this.todo_list.splice(id,1);
        } 
      },

      update_todo:function(id){
         var doc = prompt("Please enter new title","New Title");
          if (doc == null || doc == "" || doc == "New Title") {         
            }else{
              this.todo_list[id] = {"title":doc,"id":id};
              this.todo_list.sort();
              console.log(doc)
              console.log(this.todo_list)
              alert('updated')
        }
      }

    
}
}

</script>