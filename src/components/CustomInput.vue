<template>
  <div class="custom-input">
    <img v-if="icon" :src="icon" :alt="this.$slots.default()[0].children">
    <label class="custom-input__label" :for="name">
      <slot />
    </label>
    <input class="custom-input__input" 
      :id="name" 
      :name="name"
      :placeholder="this.$slots.default()[0].children" 
      v-model="text" 
      @change="textChange"
    />
  </div>
</template>

<script>
export default {
  name: 'CustomInput',
  props: {
    name: String,
    icon: String,
  },
  created() {
  },
  data() {
    return {
      text: ''
    }
  },
  methods: {
    textChange(e) {
      this.$parent.textChange(e)
    }
  }
}
</script>

<style scoped>
  .custom-input {
    margin-bottom: 0.5em;
    width: 100%;
    border: 1px solid lightgray;
    border-radius: 4px;
    height: 3em;
  }
  .custom-input__label {
    display: none;
  }
  .custom-input__input, .custom-input__input:focus {
    border: none;
    outline: none;
  }
  .custom-input__input {
    width: inherit;
    font-size: 1em;
    border-radius: inherit;
    padding: 0px 15px;
    box-sizing: border-box;
    height: 100%;
  }
</style>
