<template>
    <div class="main-page" key="pageLoaded">
        <div class="todo-container">
                <transition-group name="move" tag="div">
                <div class="todo" v-for="(el, i) in currentPage" :key="`${i}-${el.id}`">
                    <div class="title"> {{el.title}}</div>
                </div>
                </transition-group>
        </div>
            <Pagination 
                :totalPages="totalPages"
                :pageLoaded="pageLoaded"
                @pageChange="changePage" /> 
    </div>
</template>

<script>
import Todos from '../../static/todo.json'
import Pagination from '../components/UI/Pagination'

export default {
    components: {
        Pagination
    },
    data() {
        return {
            todos: Todos,
            slicedTodos: [],
            elementsPerPage: 6,
            createdPages: [],
            clicked: false,
            pageLoaded: 0
        }
    },
    computed: {
        currentPage() {
            return this.slicedTodos[this.pageLoaded]
        }
    },
    methods: {
        changePage(index) {
            console.log(index)
            this.pageLoaded = index
        }
    },
    created() {
        if(this.todos.length > 0 && this.todos != null) {
            console.log(this.todos)
            for (let i = 0; i < this.todos.length; i += this.elementsPerPage) {
                this.slicedTodos.push(this.todos.slice(i, i + this.elementsPerPage));
            }
            this.totalPages = this.slicedTodos.length
            }
        } 
    }


</script>

<style scoped>
.main-page {
    width: 100%;
    height: 100%;
    display: flex;
    flex-flow: column;
    align-items: center;
    align-content: center;
}
.todo-container {
    display: flex;
    flex-wrap: wrap;
    align-content: center;
    justify-content: center;
    max-width: 100%;
    position: absolute;
    top: 5em;
    left: 0;
}

button {
    margin: 0 1em;
}
.page {
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    align-content: center;
}

.todo {
    display: flex;
    padding: 1em;
    margin: 1em 3em;
    border: 1px solid black;
    border-radius: 5px;
    transition: all .4s;
    position: static;
    
}
.title {
    
}
.move-enter {
  /* transform: translateY(10%); */
  opacity: 0;
}
.move-enter-to {
        
	/* transform: translateY(0); */
    opacity: 1;
	
}
.move-enter-active { 
    /* transform: translateX(100%); */
	transition: all .4s;
 
}
.move-leave {
   transform: translateX(100%);
}
.move-leave-to {

opacity: 0;	
}
.move-leave-active {
    /* display: none; */
    /* position: absolute; */
    transition: all .1s;
}
.move-move {
    /* transition: all 1.5s; */
}


</style>