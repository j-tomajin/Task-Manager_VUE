<script>
    export default {
        name: 'Button',
        props: {
            text: {
                type: String,
                default: 'This is a button'
            },
            color: {
                type: String,
                default: 'green'
            }
        }
    }
</script>

<template>
    <button
        @click="$emit('btn-click')"
        :style="{background: color}"
    >
        {{ text }}
    </button>
</template>

<style scoped lang="scss">
    button {
        outline: 0;
        border: none;
        padding: 12px 16px;
        color: white;
        border-radius: 4px;
    }
</style>