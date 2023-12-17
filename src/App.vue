<template>
  <div class="view">
    <create-form>
      <template v-slot:header>
        <h3>Данные</h3>
      </template>
      <select-input name="manager" icon="user.png" selectType="alt" label="Менеджер" :showLabel="true" :options="['Менеджер 1', 'Менеджер 2', 'Менеджер 3']">Нет пользователя</select-input>
      <custom-input name="productName">Название продукта</custom-input>
      <custom-input name="jiraLink">Ссылка в Jira</custom-input>
      <select-input name="domen" :options="['Бэк-офис', 'Техплатформа', 'Офис больших данных', 'Цифровой опыт поставщика']">Домен</select-input>
    </create-form>
    <create-form>
      <template v-slot:header>
        <h3>Создать сотрудника</h3>
      </template>
      <select-input name="employee" icon="user.png" selectType="alt" label="Сотрудник" :showLabel="true" :options="['Сотрудник 1', 'Сотрудник 2', 'Сотрудник 3']">Нет пользователя</select-input>
      <select-input name="supervisor" icon="user.png" selectType="alt" label="Руководитель" :showLabel="true" :options="['Руководитель 1', 'Руководитель 2', 'Руководитель 3']">Нет руководителя</select-input>
      <select-input name="bidType" :options="['opex', 'sapex']">Тип ставки</select-input>
      <select-input name="buisenessType" :options="['MVM', 'MTech']">Бизнес единица</select-input>
      <number-input name="productName" :min="0" :max="100">Процент капитализации</number-input>
      <custom-input name="jobTitle">Должность</custom-input>
    </create-form>
  </div>
  <div class="view">
    <create-form :cols="2">
      <template v-slot:header>
        <h3>Данные</h3>
      </template>
      <select-input name="manager" icon="user.png" selectType="alt" label="Менеджер" :showLabel="true" :options="['Менеджер 1', 'Менеджер 2', 'Менеджер 3']">Нет пользователя</select-input>
      <select-input name="domen" :options="['Бэк-офис', 'Техплатформа', 'Офис больших данных', 'Цифровой опыт поставщика']">Домен</select-input>
      <custom-input name="productName">Название продукта</custom-input>
      <custom-input name="jiraLink">Ссылка в Jira</custom-input>
    </create-form>
    <create-form :cols="3">
      <template v-slot:header>
        <h3>Создать сотрудника</h3>
      </template>
      <select-input name="employee" icon="user.png" selectType="alt" label="Сотрудник" :showLabel="true" :options="['Сотрудник 1', 'Сотрудник 2', 'Сотрудник 3']">Нет пользователя</select-input>
      <select-input name="supervisor" icon="user.png" selectType="alt" label="Руководитель" :showLabel="true" :options="['Руководитель 1', 'Руководитель 2', 'Руководитель 3']">Нет руководителя</select-input>
      <select-input name="bidType" :options="['opex', 'sapex']">Тип ставки</select-input>
      <select-input name="buisenessType" :options="['MVM', 'MTech']">Бизнес единица</select-input>
      <number-input name="productName" :min="0" :max="100">Процент капитализации</number-input>
      <custom-input name="jobTitle">Должность</custom-input>
    </create-form>
  </div>
</template>

<script>
import CreateForm from './components/CreateForm.vue'
import CustomInput from './components/CustomInput.vue';
import SelectInput from './components/SelectInput.vue';
import NumberInput from './components/NumberInput.vue';

export default {
  name: 'App',
  components: {
    CreateForm,
    CustomInput,
    SelectInput,
    NumberInput,
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
  .view {
    display: flex;
    gap: 30px;
  }
</style>
