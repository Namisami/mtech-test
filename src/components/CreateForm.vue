<template>
  <form class="create-form" @submit="submit" method="post">
    <slot name="header" />
    <slot />
    <div class="create-form__footer">
      <button class="create-form__btn create-form__cancel">
        ОТМЕНА
      </button>
      <input class="create-form__btn" 
        :disabled="Object.keys($slots.default()).length !== Object.keys(this.formData).length" 
        type="submit" 
        value="СОЗДАТЬ" 
      />
    </div>
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
  created() {
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
  .create-form {
    width: 100%;
  }
  .create-form__btn {
    display: block;
    cursor: pointer;
    background: rgb(199, 14, 199);
    color: white;
    border: none;
    border-radius: 5px;
    width: min-content;
    padding: 0.5em 0.5em;
    font-size: 1.5em;
  }
  .create-form__cancel {
    background: transparent;
    color: black;
  }
  .create-form__btn:disabled {
    cursor: auto;
    opacity: 0.5;
  }
  .create-form__footer {
    display: flex;
    justify-content: end;
    gap: 1em;
  }
</style>
