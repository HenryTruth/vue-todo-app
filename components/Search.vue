<template>
    <div class="header__input">
        <form  @submit.prevent="onSubmit">
            <input 
            type="text"
            v-model="search"
            />
            <button>ADD TASK</button>
            <div>
                <!-- {{id}} -->
            </div>
        </form>
    </div>
</template>

<script>
import { v4 as uuidv4 } from 'uuid';
export default {
    data(){
        return{
            search:'',
        }
    },
    methods:{
        onSubmit(){
            const newTodo = {
                // id:uuidv4(),
                title:this.search,
                completed:false,
                
            }
            this.$emit('value', newTodo)
            this.search = ""
        }
        
    },
    computed:{

    }
}
</script>

<style lang="less" scoped>
.header__input{
    input{
        width: 22rem;
        height: 2.5rem;
        display:inline;
    }
    button{
        width: 7rem;
        height: 2.8rem;
        margin-left: 1rem;
        color: white;
        background-color: #3C9671;
        border: none;
        font-size: 1rem;
        &:hover{
            cursor: pointer;
        }
    }
}
</style>