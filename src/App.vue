<template>
  <div>
    <create-form>
      <select-input name="manager" icon="user.png" selectType="alt" label="Менеджер" :showLabel="true" :options="['Менеджер 1', 'Менеджер 2', 'Менеджер 3']">Нет пользователя</select-input>
      <custom-input name="productName">Название продукта</custom-input>
      <custom-input name="jiraLink">Ссылка в Jira</custom-input>
      <select-input name="domen" :options="['Бэк-офис', 'Техплатформа', 'Офис больших данных', 'Цифровой опыт поставщика']">Домен</select-input>
    </create-form>
  </div>
</template>

<script>
import CreateForm from './components/CreateForm.vue'
import CustomInput from './components/CustomInput.vue';
import SelectInput from './components/SelectInput.vue';

export default {
  name: 'App',
  components: {
    CreateForm,
    CustomInput,
    SelectInput
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  font-size: 16px;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
