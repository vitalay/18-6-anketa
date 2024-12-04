<template>
  <div class="container">
    <form class="card" @submit.prevent="submitHandler">
      <h1>Анкета на VUE разработчика!</h1>
      <div class="form-control">
        <label for="name">Как тебя зовот</label>
        <input 
        type="text"
         id="name" 
         placeholder="Введите имя"
         v-model.trim="name" 
         />
      </div>

      <div class="form-control">
        <label for="age">Выбери возраст</label>
        <input
         type="number"
         id="age" 
         max="70"
         v-model.number="age"
          />
      </div>

      <div class="form-control">
        <label for="city">Твой город</label>
        <select id="sity" v-model="city">
          <option value="spb">Санкт-Петербург</option>
          <option value="msk">Москва</option>
          <option value="kzn">Казань</option>
          <option value="nsk">Новосибирск</option>
        </select>
      </div>

      <div class="form-checkbox">
        <span>Готовы к переезду в Токио?</span>
        <div class="checkbox">
          <label><input type="radio" v-model="relocation" name="trip" value="yes"/>Да</label>
        </div>
        <div class="checkbox">
          <label><input type="radio"  v-model="relocation" name="trip" value="no" />Нет</label>
        </div>
      </div>

      <div class="form-checkbox">
        <span class="label"  >Что знаеш о Vue?</span>
        <div class="checkbox">
          <label><input type="checkbox" v-model="skills" name="skills" value="Vuex" />Vuex</label>
        </div>
        <div class="checkbox">
          <label><input type="checkbox" v-model="skills" name="skills" value="Vue CLI" />Vue CLI</label>
        </div>
        <div class="checkbox">
          <label><input type="checkbox"  v-model="skills" name="skills" value="Vuex Router" />Vuex Router</label>
        </div>
      </div>

      <button type="submit" class="btn-primary">Отправить</button>
    </form>
  </div>
</template>

<script>
export default {
    data() {
        return {
         name: '',
         age: 23,
         city: 'nsk',
         relocation: null,
         skills: []
        }
    },
  methods: {
    submitHandler() {
        console.group('Form data');
        console.log('Name:', this.name);
        console.log('Age:', this.age);
        console.log('City:', this.city);
        console.log('To Tokyo:', this.relocation);
        console.log('skills:', this.skills);
        console.groupEnd();
      

    }
    
  },
};
</script>

<style scoped></style>
