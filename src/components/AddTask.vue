<template>
    <form @submit="onSubmit" class="form">
        <!-- text -->
        <div class="form-container">
            <label>Task</label>
            <input 
                type="text"
                name="text"
                v-model="text"
                placeholder="Add new task...">
        </div>
        
        <!-- day -->
        <div class="form-container">
            <label>Day</label>
            <input 
                type="text"
                name="day"
                v-model="day"
                placeholder="Time and Date">
        </div>

        <!-- reminder -->
        <div class="form-reminder">
            <label for="reminder">Set Reminder</label>
            <input 
                id="reminder"
                type="checkbox"
                name="reminder"
                v-model="reminder"
            >
        </div>

        <input 
            type="submit"
            value="Save Task"
            class="submit-btn"
        />
    </form>
</template>

<script>
    export default {
        name: 'AddTask',
        data() {
            return {
                text: '',
                day: '',
                reminder: false
            }
        },
        methods: {
            onSubmit(e) {
                e.preventDefault() 
                if(!this.text || !this.day) {
                    alert('Please add a task, date and time')
                    return
                }

                const newTask = {
                    id: Math.floor(Math.random() * 100000),
                    text: this.text,
                    day: this.day,
                    reminder: this.reminder
                }

                this.$emit('new-task', newTask)

                this.text = ''
                this.day = ''
                this.reminder = false
            }
        }
    }
</script>

<style lang="scss" scoped>
    .form {
        margin-bottom: 32px;
    }
    .form-container {
        width: 100%;
        margin-bottom: 12px;

        input {
            width: 100%;
            padding: 8px 12px;
            outline: 0;
            border: none;
        }
    }
    .form-reminder {
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 24px;
        margin-bottom: 16px;

        label:hover {
            text-decoration: underline;
        }

        label, 
        input {
            cursor: pointer;
        }
    }

    .submit-btn {
        display: block;
        margin-inline: auto;

        width: 50%;
        padding: 10px 24px;
        border-radius: 8px;
        outline: 0;
        border: 0;
        background-color: rgb(20, 126, 20);
        color: white;
        cursor: pointer;
    }
</style>