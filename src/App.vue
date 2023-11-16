<template>
 <div class="">
Задача 1. Розробити компонент для введення віку користувача (з підтримкою v-model).<br>
 При заданні модифікатора check не допускати введення некоректного віку (вік не може бути більшим за 150).<br> 
 При заданні модифікатора setColor задавати фон (вік менше 10 – зелений, від 10 до 21 – жовтий, інакше – оранжевий). 
Задача 2. Розробити компонент (з підтримкою v-model), який дозволяє вводити шлях до файлу js (URL, що закінчується<br>
 розширенням js). При заданні модифікатора checkPath відображати червоним фоном input, якщо шлях некоректний.
Задача 3. Розробити компонент (з підтримкою v-model), який дозволяє вводити e-mail з домену “edu”<br> 
(приклад: ivan-hopko@inv.mn.edu). Частинка «@inv.mn.edu» додається автоматично (користувач не вводить її).<br>
 При заданні модифікатора check відображати червоним фоном input, якщо некоректний.
Задача 4. Розробити компонент для вводу віку користувача та імені. Робити форматування при заданні відповідних<br>
 модифікаторів відповідних полів input:
ім’я користувача -  у випадку порожнього поля (червони фон) 
вік (вік менший за 18 – колір фону червоний, інакше – зелений).
 </div>
 <age-input v-model:currentUserAge.check.setColor="userAge" title="Введіть свій вік:"  />
 <path-input v-model:currentPath.checkPath="userPath"/>
 <mail-autocomplete v-model:currentMail.check="userMail" />
 <data-user v-model:currentName.checkName ="userName" v-model:currentDataUserAge.checkAge ="dataUserAge"/>
</template>

<script>
import AgeInput from './components/AgeInput.vue';
import MailAutocomplete from './components/MailAutocomplete.vue';
import PathInput from './components/PathInput.vue';
import DataUser from './components/DataUser.vue';
export default {
  name: "App",
  components: {
    AgeInput,PathInput,
    MailAutocomplete,
		DataUser

  },
  data() {
    return {
			userAge: null,
			userPath:null,
			userMail:null,
			userName:'',
			dataUserAge:null,
    }
  },

};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
