<template>
    <div class="container">
        <header>
            <div class="header__title">
                <h1>Vue js <span>Todo app</span></h1>
            </div>
            <search @Value="addTodo"/>
        </header>
        <task :todos="todos" @del-todo="deleteTodo"/>  
    </div>
</template>

<script>
import axios from 'axios'
import Card from './components/Card.vue'
import Search from './components/Search.vue'
import Task from './components/Task.vue'

var In;

export default {
    components:{
        Search,
        Task,
        Card
    },

    data(){
        return{
            todos:[
                
            ],
        }
    },

    methods:{
        addTodo(newTodo){
            const{title, completed} = newTodo;
            axios.post(`http://localhost:8000/api/todos/`, {
                title,
                completed
            })
            .then(res => this.todos = [...this.todos, res.data])
            .catch(err => console.log(err));
            console.log('successss')
            // this.todos = [...this.todos, newTodo];
        },
        deleteTodo(id){
            axios.delete(`http://localhost:8000/api/todos/${id}`)
            .then(In = this.todos.findIndex(todo => todo.id === id),
             this.todos.splice(In,1))
            .catch(err => console.log(err));
            
            
           
        },
    },
    created(){
            axios.get(`http://localhost:8000/api/todos/`)
            .then(res => this.todos = res.data)
            .catch(err => console.log(err));
            console.log('succes')
    }
}
</script>

<style lang="less" scoped>
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body{
    font-size: 62.2%;
    a{
        text-decoration: none;
    }
    
}

#app{
    display: grid;
    grid-template-rows: repeat(auto,auto);
    
    .container{
        background: #ffffff;
        display: grid;
        grid-template-rows: 45vh auto;
        grid-template-columns: 1fr;
        // min-height: 90vh;
        margin: 1rem 6rem;
        box-shadow: 3px 5px 15px grey;
        border-radius: 5px;

        header{
            display:grid;
            grid-template-columns: 1fr;
            grid-template-rows: repeat(2, 1fr);
            place-items: center;

            .header__title{
                background-color:#3C9671;
                height: 5rem;
                width: 15rem;
                border-radius: .3rem;
                h1{
                    color: white;
                    text-align: center;
                    margin: 0.8rem 0;
                    font-size: 2.6rem;
                    font-family: 'IBM Plex Sans', sans-serif;
                    span{
                        font-size: 1.3rem;
                    }
                }
            }
    
        }
    }
}
</style>