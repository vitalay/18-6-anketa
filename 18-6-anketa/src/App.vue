<template>
    <div class="container">
      <form class="card" @submit.prevent="submitHandler">
        <h1>Анкета на VUE разработчика!</h1>
        
        <!-- Поле имени -->
        <div class="form-control" :class="{ invalid: errors.name }">
          <label for="name">Как тебя зовут</label>
          <input
            type="text"
            id="name"
            placeholder="Введите имя"
            v-model.trim="name"
          />
          <small v-if="errors.name">{{ errors.name }}</small>
        </div>
  
        <!-- Возраст -->
        <div class="form-control">
          <label for="age">Выбери возраст</label>
          <input
            type="number"
            id="age"
            max="70"
            min="18"
            v-model.number="age"
          />
        </div>
  
        <!-- Город -->
        <div class="form-control">
          <label for="city">Твой город</label>
          <select id="city" v-model="city">
            <option value="spb">Санкт-Петербург</option>
            <option value="msk">Москва</option>
            <option value="kzn">Казань</option>
            <option value="nsk">Новосибирск</option>
          </select>
        </div>
  
        <!-- Переезд в Токио -->
        <div class="form-checkbox">
          <span>Готовы к переезду в Токио?</span>
          <div class="checkbox">
            <label><input type="radio" v-model="relocation" name="trip" value="yes" />Да</label>
            <label><input type="radio" v-model="relocation" name="trip" value="no" />Нет</label>
          </div>
        </div>
  
        <!-- Навыки -->
        <div class="form-checkbox">
          <span class="label">Что знаешь о Vue?</span>
          <div class="checkbox">
            <label><input type="checkbox" v-model="skills" value="Vuex" />Vuex</label>
            <label><input type="checkbox" v-model="skills" value="Vue CLI" />Vue CLI</label>
            <label><input type="checkbox" v-model="skills" value="Vue Router" />Vue Router</label>
          </div>
        </div>
  
        <!-- Согласие -->
        <div class="form-checkbox">
          <span class="label">Правила нашей компании</span>
          <div class="checkbox">
            <label><input type="checkbox" v-model="agree" />С правилами согласен</label>
          </div>
        </div>
  
        <!-- Кнопка -->
        <button type="submit" class="btn-primary">Отправить</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        name: "",
        age: 23,
        city: "nsk",
        relocation: "no",
        skills: [],
        agree: false,
        errors: {
          name: null,
          agree: null,
          skills: null,
        },
      };
    },
    methods: {
      formIsValid() {
        let isValid = true;
  
        // Валидация имени
        if (this.name.length === 0) {
          this.errors.name = "Поле не может быть пустым";
          isValid = false;
        } else {
          this.errors.name = null;
        }
  
        // Валидация соглашения
        if (!this.agree) {
          this.errors.agree = "Вы должны согласиться с правилами";
          isValid = false;
        } else {
          this.errors.agree = null;
        }
  
        // Валидация навыков
        if (this.skills.length === 0) {
          this.errors.skills = "Выберите хотя бы один навык";
          isValid = false;
        } else {
          this.errors.skills = null;
        }
  
        return isValid;
      },
      submitHandler() {
        if (this.formIsValid()) {
          console.group("Form data");
          console.log("Name:", this.name);
          console.log("Age:", this.age);
          console.log("City:", this.city);
          console.log("To Tokyo:", this.relocation);
          console.log("Skills:", this.skills);
          console.log("Agree:", this.agree);
          console.groupEnd();
          alert("Форма отправлена успешно!");
        } else {
          alert("Пожалуйста, заполните форму корректно.");
        }
      },
    },
  };
  </script>
  
  <style scoped>
  .container {
    max-width: 600px;
    margin: 0 auto;
  }
  
  .card {
    background-color: #f9f9f9;
    border: 1px solid #ddd;
    border-radius: 6px;
    padding: 1.5rem;
  }
  
  .form-control {
    margin-bottom: 1rem;
  }
  
  .form-control.invalid input {
    border-color: #d9534f;
  }
  
  .form-control small {
    color: #d9534f;
  }
  
  .form-checkbox {
    margin-bottom: 1rem;
  }
  
  .btn-primary {
    background-color: #007bff;
    color: white;
    border: none;
    padding: 0.5rem 1rem;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .btn-primary:hover {
    background-color: #0056b3;
  }
  </style>
  