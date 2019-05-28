<template>
    <div id = 'ToDoList'>
        <input v-model="todo">
        <button @click="add()">+增加</button>
        <br>
        <hr>
        <h2>进行中</h2>
        <ul>
            <li v-for="(item,key) in list " v-if="!item.checked">
                <input type="checkbox" v-model="item.checked">{{item.title}}<button @click="deleteTodo(key)">删除</button>
            </li>
        </ul>
        <br>
        <hr>
        <h2>已完成</h2>
        <ul>
            <li v-for="(item,key) in list "v-if="item.checked">
                <input type="checkbox" v-model="item.checked">{{item.title}}<button @click="deleteTodo(key)">删除</button>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        data(){
            return {
                todo: '',
                list:[],
            }
            },methods:{
                add(){
                    const e = {
                        title:this.todo,
                        checked:false
                    };
                    this.list.push(e);
                    this.todo = '';
                }, deleteTodo(index){
                    this.list.splice(index,1);
                 },finish(e){
                    this.list[e].checked
            }
        }
    }
</script>

<style scoped>

</style>