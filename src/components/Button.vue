<template>
        <button 
            class="button is-outlined is-fullwidth is-dark"
            @click="event"
            v-html="text"
            :disabled="disabled"
        />
</template>

<script>
export default {
    name: 'Button',
    
    props: {
        text: { 
            type: String,
        },
        event: {
            type: Function,
            required: true,
        },
        disabled: {
            type: Boolean,
            default: false,
        }
    },
}
</script>