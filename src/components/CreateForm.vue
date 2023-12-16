<template>
  <form class="create-form" @submit="submit" method="post">
    <slot v-for="(slot, index) of Object.keys($slots)" :key="index"></slot>
    <input class="create-form__btn" :disabled="Object.keys($slots.default()).length !== Object.keys(this.formData).length" type="submit" value="СОЗДАТЬ" />
  </form>
</template>

<script>
export default {
  name: 'CreateForm',
  data() {
    return {
      formData: {}
    }
  },
  methods: {
    textChange(e) {
      this.formData[e.target.name] = e.target.value
    },
    submit(e) {
      e.preventDefault()
      console.log(this.formData)
    }
  }
}
</script>

<style>
  .create-form__btn {
    display: block;
    cursor: pointer;
    background: rgb(199, 14, 199);
    color: white;
    border: none;
    border-radius: 5px;
    padding: 0.5em 0.5em;
    font-size: 1.5em;
    margin-left: auto;
  }
  .create-form__btn:disabled {
    opacity: 0.5;
  }
</style>
