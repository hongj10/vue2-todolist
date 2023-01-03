<template>
    <li class="tasks__item">
        <button :class="['tasks__item__toggle', {'tasks__item__toggle--completed': todo.isCompleted}]" @click="$emit('complete1')">
            {{ todo.title }} {{ todo.isCompleted }}
        </button>        

        <button class="tasks__item__remove button alert pull-right" @click="$emit('remove1')">
            <i class="fa fa-times"></i>
        </button>
    </li>
</template>

<script>
export default {
    props: {
        todo: {
            type: Object,
            default: () => { },
        },
    },
    methods: {
    },
}
</script>

<style lang="scss" scoped>

</style>