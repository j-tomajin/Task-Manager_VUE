<template>
    <div class="header">
        <h1>{{ text }}</h1>
        <Button 
            @btn-click="$emit('toggle-add-task')" 
            :text="showAddTask ? 'Close' : 'Add task'"
            :color="showAddTask ? 'red' : 'green'"
            />
    </div>
</template>

<script>
    import Button from './Button.vue';

    export default {
        name: 'Header',
        props: {
            text: {
                type: String,
                default: 'This is Header',
            },
            showAddTask: Boolean
        },
        components: {
            Button,
        }
    }
</script>

<style scoped lang="scss">
    .header {
        display: flex;
        align-items: center;
        justify-content: space-between;

        margin-block: 16px;
    }
</style>