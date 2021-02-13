<template>
<div class="field">
  <p :class="['control', hasIcon() ? 'has-icons-left' : '']">
    <input 
      :class="['input', `is-${color}`]" 
      :type="type" 
      :value="value"
      :placeholder="placeholder" 
      @input="$emit('input', $event.target.value)" 
      @change="emitValue" 
    />
    <span class="icon is-small is-left" v-if="hasIcon()" v-html="displayIcon()"></span>
  </p>
</div>
</template>

<script>
export default {
  name: 'Input',

  props: {
    type: {
      type: String,
      required: true,
    },
    placeholder: {
      type: String,
      required: true,
    },
    color: {
      type: String,
      default: 'dark',
    },
    icon: {
      type: String,
    },
    value: {
      type: [String, Number],
    }
  },

  data() {
    return { model: null }
  },

  methods: {
    displayIcon() {
      return this.hasIcon() ? `<i class="fas fa-${this.icon}"></i></span>` : ''
    },

    hasIcon() {
      return this.icon
    },

    emitValue() {
      this.$emit('change', this.value)
    },

  },
}
</script>

<style scoped>
/* Chrome, Safari, Edge, Opera */
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

/* Firefox */
input[type=number] {
  -moz-appearance: textfield;
}
</style>