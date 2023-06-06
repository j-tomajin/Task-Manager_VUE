<template>
    <div
        class="task"
        v-for="task in tasks"
        :key="task.id"
    >
        <Task 
            @delete-task="$emit('delete-task', task.id)"
            @toggle-reminder="$emit('toggle-reminder', task.id)"
            :task="task" />
    </div>
    <p>Nothing follows</p>
</template>

<script>
    import Task from './Task.vue';

    export default {
        name: 'Tasks',
        props: {
            tasks: Array,
        },
        components: {
            Task,
        },
        emits: ['delete-task', 'toggle-reminder']
    }
</script>

<style lang="scss" scoped>
    p {
        text-align: center;
    }
</style>