<template>
  <div class="custom-input">
    <img class="custom-input__icon" v-if="icon" :src="icon" :alt="this.$slots.default()[0].children">
    <label v-if="label" class="custom-input__label" :class="{ paddingIcon: showLabel, hiden: !showLabel }" :for="name" >
      {{ label }}
    </label>
    <label v-else class="custom-input__label" :class="{ paddingIcon: showLabel, hiden: !showLabel }" :for="name" >
      <slot />
    </label>
    <input class="custom-input__input" 
      :class="{ withIcon: icon }"
      :id="name" 
      :name="name"
      :placeholder="this.$slots.default()[0].children"
      v-model="text" 
    />
    <div v-if="selectType === 'alt'" class="plus" :class="{ arrowOpen: open }" />
    <div v-else class="arrow-down" :class="{ arrowOpen: open }" />
    <div class="custom-input__selected" @click="open = !open" />
    <div class="custom-input__items" :class="{ selectHide: !open }">
      <div
        class="custom-input__item"
        v-for="(option, i) of options"
        :key="i"
        @click="
          open = false;
          text = option
        "
      >
        {{ option }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SelectInput',
  props: {
    name: String,
    icon: String,
    options: Array,
    label: String,
    selectType: String,
    showLabel: Boolean,
  },
  created() {
  },
  data() {
    return {
      text: '',
      open: false,
    }
  },
  watch: {
    text(value) {
      this.$parent.textChange({ target: { name: this.$props.name, value: value }})
    }
  }
}
</script>

<style scoped>
  .custom-input {
    margin-bottom: 0.5em;
    height: 3em;
    width: 100%;
    border: 1px solid lightgray;
    border-radius: 4px;
    position: relative;
    text-align: left;
  }
  .custom-input__label {
    position: absolute;
    left: calc(15px);
    top: 4px;
    font-size: 0.7em;
  }
  .paddingIcon {
    left: calc(30px + 1.5rem);
  }
  .hiden {
    display: none;
  }
  .custom-input__input, .custom-input__input:focus {
    border: none;
    outline: none;
  }
  .custom-input__input {
    height: 3em;
    width: inherit;
    font-size: 1em;
    border-radius: inherit;
    padding: 0px 15px;
    border-bottom: 1px solid lightgray;
    box-sizing: border-box;
  }
  .custom-input__selected {
    position: absolute;
    top: 0;
    cursor: pointer;
    height: inherit;
    width: inherit;
    user-select: none;
  }
  .custom-input__selected:after {
    position: absolute;
    content: "";
    top: 22px;
    right: 1em;
    width: 0;
    height: 0;
    z-index: 5;
  }
  .custom-input__item {
    height: inherit;
    padding: 0px 15px;
    display: flex;
    background: white;
    align-items: center;
    border: 1px solid lightgray;
    border-top: 0;
    cursor: pointer;
  }
  .custom-input__item:last-child {
    border-radius: 0 0 4px 4px;
  }
  .custom-input__item:hover {
    background: rgb(207, 243, 255);
  }
  .custom-input__items {
    /* overflow: hidden; */
    position: absolute;
    left: 0;
    right: 0;
    z-index: 1;
    height: inherit;
  }
  .selectHide {
    display: none;
  }
  .withIcon {
    padding: 0px calc(30px + 1.5em);
  }
  .plus {
    filter: opacity(40%);
    position: absolute;
    display:inline-block;
    width:1.5em;
    height:1.5em;
    top: 50%;
    transform: translateY(-50%);
    right: 15px;
    background: 
      linear-gradient(#000,#000),
      linear-gradient(#000,#000);
    background-position:center;
    background-size: 50% 2px,2px 50%; /*thickness = 2px, length = 50% (25px)*/
    background-repeat:no-repeat;
  }
  .arrow-down {
    width: 0; 
    height: 0; 
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    right: 15px;
    border-left: 8px solid transparent;
    border-right: 8px solid transparent; 
    border-top: 8px solid lightgray;
    z-index: 0;
  }
  .custom-input__icon {
    filter: opacity(40%);
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    left: 15px;
    width: 1.5em;
    height: 1.5em;
  }
  .arrowOpen {
    display: none;
  }
</style>
