<template>
  <div class="form-control" :class="{ invalid:error }">
    <label :for="id">{{ label }}</label>
    <input
        type="text"
        :id="id"
        :placeholder="myPlaceholder"
        :value="value"
        @input="change"
    >
    <small v-if="error">{{ error }}</small>
  </div>
</template>

<script>
export default {
  emits: [
    'update:value'
  ],
  props: {
    error: {
      type: String,
      required: true
    },
    label: {
      type: String,
      required: true
    },
    myPlaceholder: {
      type: String,
      required: true
    },
    value: {
      type: String,
      required: true
    }
  },
  data(){
    return {
      id: 'input-' + Math.random()
    }
  },
  methods: {
    change(event){
      this.$emit('update:value', event.target.value)
    }
  }
}
</script>

<style scoped>

</style>