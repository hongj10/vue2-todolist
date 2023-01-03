<template>
    <section class="tasks">
        <h1>
            Tasks
            <small>(1)</small>
        </h1>
        <div class="tasks__new input-group">
            <input type="text" class="input-group-field" placeholder="New task" v-model="newTodo">
            <span class="input-group-button">
                <button class="button" @click="addTodo"><i class="fa fa-plus"></i> Add</button>
            </span>
        </div>

        <div class="tasks__clear button-group pull-right">
            <button class="button warning small"><i class="fa fa-check"></i> Clear Completed</button>
            <button class="button alert small"><i class="fa fa-trash"></i> Clear All</button>
        </div>

        <ul class="tasks__list no-bullet">
            <TodoItem v-for="(todo, index) in todos"
                :todo="todo"
                :key="index"
                @complete1="onComplete(todo)"  
                @remove1="onRemove(index)"            
            />
        </ul>
    </section>
</template>

<script>
import TodoItem from './TodoItem.vue';

export default {
    components: {
        TodoItem,
    },
    data() {
        return {
            todos: [
                {
                    title: '할일 1',
                    isCompleted: true,
                },
                {
                    title: '할일 2',
                    isCompleted: false,
                }
            ],
            newTodo: '',
        }
    },
    methods:{
        addTodo() {
            console.log('addtodo', this.newTodo)
            this.todos.push({
                title: this.newTodo,
                isCompleted: false
            });
            this.newTodo = '';            
        },
        // clearComplete () {
        //     // this.todos = this.todos.filter(todo => !todo.isCompleted);
        //     const aaaa = this.todsfileter(function(todo) {
        //         return !todo.isCompleted;
        //     });
        //     this.todos = aaaa;
        // },
        // onClearAll () {
        //     this.todos = [];
        // },
        // onComplete() {
        //     this.$emit('complete')
        // }
        
        // // onClearComplte (){
        // //     this.c
        // // }
        onComplete(todo) {
            todo.isCompleted = !todo.isCompleted;
        },
        onRemove(index) {
            this.todos.splice(index, 1);
        }
    }
}
</script>

<style>
body {
    background-color: #abc;
}

*,
h1,
button {
    font-family: 'Nunito', sans-serif;
}

.fade-enter-active,
.fade-leave-active {
    transition: opacity .5s
}

.fade-enter,
.fade-leave-active {
    opacity: 0
}

.tasks {
    width: 100%;
    max-width: 45rem;
    padding: 1em;
    margin: 1em auto;
    overflow: auto;
    background-color: white;
    box-shadow: 0px .25rem 1rem rgba(black, .25);
}

.tasks__list {
    clear: both;
}

.tasks__item {
    margin-bottom: .5em;
    position: relative;
}

.tasks__item__toggle {
    cursor: pointer;
    width: 100%;
    text-align: left;
    padding: 0.85em 2.25em 0.85em 1em;
    background-color: rgba(0, 0, 0, 0.05);
    border: 1px solid rgba(0, 0, 0, 0.1);
}

.tasks__item__toggle:hover {
    background-color: rgba(black, .1);
    border-color: rgba(black, .15);
}

.tasks__item__toggle--completed {
    text-decoration: line-through;
    background-color: rgba(0, 128, 0, 0.15);
    border-color: rgba(0, 128, 0, 0.2);
}

.tasks__item__toggle--completed:hover {
    background-color: rgba(green, .25);
    border-color: rgba(green, .3);
}

.tasks__item__remove {
    position: absolute;
    height: 100%;
    top: 50%;
    right: 0;
    transform: translateY(-50%);
}

.tasks__item__remove i {
    vertical-align: middle
}
</style>