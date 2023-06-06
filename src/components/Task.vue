<template>
    <div 
        :class="[task.reminder ? 'reminder' : '', 'tasks']"
        @dblclick="$emit('toggle-reminder', task.id)"
    >
        <div>
            <h3>{{ task.text }}</h3>
            <span>{{ task.day }}</span>
        </div>

        <i 
            class="fa-solid fa-circle-xmark"
            @click="$emit('delete-task', task.id)"    
        >
        </i>
    </div>
</template>

<style lang="scss" scoped>
    .fa-solid {
        color: rgb(255, 47, 47);
        font-size: 24px;
        cursor: pointer;
    }

    .tasks {
        background-color: #444;
        margin-bottom: 16px;
        padding: 12px 24px;
        display: flex;
        align-items: center;
        justify-content: space-between;
    }

    h3 {
        color: whitesmoke;
        text-transform: uppercase;
        letter-spacing: 1.5px;
    }

    span {
        color: rgb(207, 207, 207);
    }

    .reminder {
        position: relative;

        &::after {
            content: '';
            position: absolute;
            left: 7.5px;
            background-color: green;
            width: 5px;
            height: 100%;
        }
    }
</style>

<script>
    export default {
        name: 'Task',
        props: {
            task: Object,
        }
    }
</script>
