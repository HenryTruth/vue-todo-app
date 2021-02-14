<template>
    <main>
        <card v-for="todo in todos" :key="todo.id" @dblclick="isShow(todo)">
            <template v-slot:content>
                    <p>{{todo.title}}</p>
                    <i class="far fa-trash-alt trash" @click="delTodo(todo.id)"></i>
                    <i :class="{'far fa-check-circle circle':todo.completed}"></i>
            </template>
        </card>
    </main>
</template>

<script>
import Card from './Card.vue'
export default {
    components:{
        Card
    },
    props:{
        todos:{
            type:Object
        }
    },
    methods:{
        isShow(todo){
            todo.completed = !todo.completed
        },
        
        delTodo(id){
            this.$emit('del-todo', id)
        }
    }
}
</script>

<style lang="less" scoped>
main{
    min-height: 15rem;
    // height: fit-content;
    background-color: #3C9671;
    margin: 1rem 7rem;
    border-radius: .3rem;
    display: grid;
    grid-template-columns:repeat(3,1fr);
p{
    text-align: center;
    font-size: 1.1rem;
}

.circle{
    color: green;
    font-size: 1.3rem;
    transform: translateX(180px) translateY(20px);
}
.trash{
    transform: translateX(-10px) translateY(20px);
    margin-left: 1rem;
    color:#C12231;
    font-size: 1.3rem;
    cursor:pointer;
    transition: .2s;

    &:hover{
        font-size: 1.7rem;
    }  
}
}
</style>