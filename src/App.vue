<template>
   <form @submit.prevent="someAction()">
     <h2 align="center">Форма создания клиента:</h2>
     <div class="form-group">
        <label for="firstName"></label>
        <input
          id="fistName"
          type="text"
          v-model="firstName"
          placeholder="Фамилия*"
          @blur="$v.firstName.$touch()"
        >
        <div class="error" v-if="$v.firstName.$error">
          <template v-if="!$v.firstName.maxLength">
            Длина имени не должна превышать {{ $v.fistName.$params.maxLength.max }} символов
          </template>
          <template v-else-if="!$v.firstName.alpha">
           Имя должно содержать только буквы
          </template>
          <template v-else>
           Имя обязательно для заполнения
          </template>
        </div>
      </div>
      <div class="form-group">
        <label for="name"></label>
        <input
          id="name"
          type="text"
          v-model="name"
          placeholder="Имя*"
          @blur="$v.name.$touch()"
        >
        <div class="error" v-if="$v.name.$error">
          <template v-if="!$v.name.maxLength">
            Длина имени не должна превышать {{ $v.name.$params.maxLength.max }} символов
          </template>
          <template v-else-if="!$v.name.alpha">
           Имя должно содержать только буквы
          </template>
          <template v-else>
           Имя обязательно для заполнения
          </template>
        </div>
      </div>
      <div class="form-group">
        <label for="lastName"></label>
        <input
          id="lastName"
          type="text"
          placeholder="Отчество"
          v-model="lastName"
          @blur="$v.lastName.$touch()"
        >
        <div class="error" v-if="$v.lastName.$error">
          <template v-if="!$v.lastName.maxLength">
            Длина имени не должна превышать {{ $v.lastName.$params.maxLength.max }} символов
          </template>
          <template v-else-if="!$v.lastName.alpha">
            Имя должно содержать только буквы
          </template>
          <template v-else>
            Имя обязательно для заполнения
          </template>
        </div>
      </div>
      <div class="form-group">
        <label for="birthdayDate">
        </label>
          <input
          id="birthdayDate"
          type="text"
          placeholder="Дата рождения*"
          v-model="birthdayDate">
          <div class="error" v-if="$v.birthdayDate.$invalid">
          Дата рождения должна быть в формате дд мм гггг
          </div>
      </div>
        <div class="form-group">
          <label for="numberPhone"></label>
            <input id="numberPhone"
            type="text"
            placeholder="Номер телефона*"
            v-model="numberPhone"
            >
              <div class="error" v-if="$v.numberPhone.$invalid">
              Номер телефона должн быть в формате 7**********
              </div>
        </div>
      <div class="form-group">
        <label for="gender"></label>
        <input
          id="gender"
          type="text"
          v-model="gender"
          placeholder="Пол"
          @blur="$v.gender.$touch()"
        >
        <div class="error" v-if="$v.gender.$error">
          <template v-if="!$v.gender.maxLength">
            Длина имени не должна превышать {{ $v.gender.$params.maxLength.max }} символов
          </template>
          <template v-else-if="!$v.gender.alpha">
           Имя должно содержать только буквы
          </template>
          <template v-else>
           Пол обязательно для заполнения
          </template>
        </div>
      </div>
      <div class="checkbox-group-checkbox">
        <input type="checkbox"
         id="VIP"
         value="VIP"
         v-model="checkedNames">
        <label for="VIP" placeholder="VIP*">VIP*</label>
        <input type="checkbox" id="Проблемные" value="Проблемные" v-model="checkedNames">
        <label for="Проблемные">Проблемные*</label>
        <input type="checkbox" id="ОМС" value="ОМС" v-model="checkedNames">
        <label for="ОМС">ОМС*</label>
        <br>
    </div>

    <div class="checkbox-group-checkbox">
      <select v-model="selected">
        <option v-for="option in options" :key="option">
          {{ option.text }}
        </option>
      </select>
      <span>Выбран врач: {{ selected }}</span>
    </div>
    <div class="checkbox-group-checkbox">
      <input type="checkbox" id="checkedSms" v-model="checkedSms">
      <label for="checkbox">Не отправлять СМС</label>
    </div>
    <h2 align="center">Адрес</h2>
      <div class="form-group">
        <label for="index"></label>
        <input
          id="index"
          type="text"
          v-model="index"
          placeholder="Индекс"
          @blur="$v.index.$touch()"
        >
        <div class="error" v-if="$v.index.$error">
          <template v-if="!$v.index.maxLength">
            Длина имени не должна превышать {{ $v.name.$params.maxLength.max }} символов
          </template>
          <template v-else-if="!$v.index.alpha">
            Имя должно содержать только буквы
          </template>
          <template v-else>
            Имя обязательно для заполнения
          </template>
         </div>
      </div>
      <div class="form-group">
        <label for="contry"></label>
        <input
          id="contry"
          type="text"
          v-model="Страна"
          placeholder="Дата рождения*"
          @blur="$v.contry.$touch()"
        >
        <div class="error" v-if="$v.contry.$error">
          <template v-if="!$v.contry.maxLength">
            Длина имени не должна превышать {{ $v.contry.$params.maxLength.max }} символов
          </template>
          <template v-else-if="!$v.contry.alpha">
            Имя должно содержать только буквы
          </template>
          <template v-else>
            Имя обязательно для заполнения
          </template>
         </div>
      </div>
      <div class="form-group">
        <label for="stateContry"></label>
        <input
          id="stateContry"
          type="text"
          placeholder="Область"
          v-model="stateContry"
          @blur="$v.stateContry.$touch()"
        >
        <div class="error" v-if="$v.stateContry.$error">
          <template v-if="!$v.stateContry.maxLength">
            Длина имени не должна превышать {{ $v.stateContry.$params.maxLength.max }} символов
          </template>
          <template v-else-if="!$v.stateContry.alpha">
            Имя должно содержать только буквы
          </template>
          <template v-else>
            Имя обязательно для заполнения
          </template>
         </div>
      </div>
      <div class="form-group">
        <label for="city"></label>
        <input
          id="city"
          type="text"
          placeholder="Город*"
          v-model="city"
          @blur="$v.city.$touch()"
        >
        <div class="error" v-if="$v.city.$error">
          <template v-if="!$v.city.maxLength">
            Длина имени не должна превышать {{ $v.city.$params.maxLength.max }} символов
          </template>
          <template v-else-if="!$v.city.alpha">
            Имя должно содержать только буквы
          </template>
          <template v-else>
            Имя обязательно для заполнения
          </template>
         </div>
      </div>
      <div class="form-group">
        <label for="street"></label>
        <input
          id="street"
          type="text"
          placeholder="Улица"
          v-model="street"
          @blur="$v.street.$touch()"
        >
        <div class="error" v-if="$v.street.$error">
          <template v-if="!$v.street.maxLength">
            Длина имени не должна превышать {{ $v.street.$params.maxLength.max }} символов
          </template>
          <template v-else-if="!$v.street.alpha">
            Имя должно содержать только буквы
          </template>
          <template v-else>
            Имя обязательно для заполнения
          </template>
         </div>
      </div>
      <div class="form-group">
        <label for="house"></label>
        <input
          id="house"
          type="text"
          placeholder="Дом"
          v-model="house"
          @blur="$v.house.$touch()"
        >
        <div class="error" v-if="$v.house.$error">
          <template v-if="!$v.house.maxLength">
            Длина имени не должна превышать {{ $v.house.$params.maxLength.max }} символов
          </template>
          <template v-else-if="!$v.house.alpha">
            Имя должно содержать только буквы
          </template>
          <template v-else>
            Имя обязательно для заполнения
          </template>
         </div>
      </div>
    <h2 align="center">Паспорт:</h2>
    <div class="form-group">
      <select v-model="selectedDoc">
        <option v-for="option in selectedDocument" :key="option">
          {{ option.text }}
        </option>
      </select>
      <span>Выбрано: {{ selectedDoc }}</span>
    </div>
    <div class="form-group">
      <label for="passport_data">
      </label>
        <input
        id="passport_data"
        type="text"
        placeholder="Серия и номер паспорта"
        v-model="passportData"
        >
        <div class="error" v-if="$v.passportData.$invalid">
          Серия и номер паспорта должны быть в формате 1234 567890
        </div>
    </div>
      <div class="form-group">
        <label for="passportIssued"></label>
        <input
          id="passportIssued"
          type="text"
          placeholder="Кем выдан*"
          v-model="passportIssued"
          @blur="$v.passportIssued.$touch()"
        >
        <div class="error" v-if="$v.passportIssued.$error">
          <template v-if="!$v.passportIssued.maxLength">
            Длина имени не должна превышать {{ $v.passportIssued.$params.maxLength.max }} символов
          </template>
          <template v-else-if="!$v.passportIssued.alpha">
            Имя должно содержать только буквы
          </template>
          <template v-else>
            Имя обязательно для заполнения
          </template>
         </div>
      </div>

      <div class="form-group">
        <label for="passportIssuedDate">
        </label>
          <input
          id="passportIssuedDate"
          type="text"
          placeholder="Дата выдачи*"
          v-model="passportIssuedDate">
          <div class="error" v-if="$v.passportIssuedDate.$invalid">
            Дата выдачи паспорта должна быть в формате дд мм гггг
          </div>
      </div>
    <button type="submit" :disabled="$v.$invalid">
      Отправить форму
    </button>
  </form>
</template>

<script>

import { required, maxLength } from 'vuelidate/lib/validators'

export default {
  data () {
    return {

      name: null,
      firstName: null,
      lastName: null,
      birthdayDate: null,
      numberPhone: null,
      gender: null,
      checkedNames: [],
      selected: 'пусто',
      options: [
        { text: 'Иванов', value: 'А' },
        { text: 'Захаров', value: 'Б' },
        { text: 'Чернышева', value: 'В' }
      ],
      checkedSms: null,
      index: null,
      contry: null,
      stateContry: null,
      city: null,
      street: null,
      house: null,
      selectedDoc: 'пусто',
      selectedDocument: [
        { text: 'Паспорт', value: 'А' },
        { text: 'Свидетельство о рождении', value: 'Б' },
        { text: 'Вод. удостоверение', value: 'В' }
      ],
      passportData: null,
      passportIssued: null,
      passportIssuedDate: null
    }
  },

  validations: {
    passportData: {
      // required,
      validFormat: val => /^\d{4} \d{6}$/.test(val)
    },
    birthdayDate: {
      // required,
      validFormat: val => /^([1-31]{2}\s{1}[1-12]{2}\s{1}[1900-2020]{4})?$/.test(val)
    },
    firstName: {
      // required,
      maxLength: maxLength(100),
      alpha: val => /^[а-яё]*$/i.test(val)
    },
    lastName: {
      required,
      maxLength: maxLength(100),
      alpha: val => /^[а-яё]*$/i.test(val)
    },
    name: {
      required,
      maxLength: maxLength(100),
      alpha: val => /^[а-яё]*$/i.test(val)
    },
    numberPhone: {
      required,
      validFormat: val => /^([7]{1}[0-9]{10})?$/.test(val)
    },
    gender: {
      required,
      maxLength: maxLength(10),
      alpha: val => /^[а-яё]*$/i.test(val)
    },
    checkedNames: {
      required
    },
    selected: {
      required
    },
    checkedSms: {
      required
    },
    index: {
      required,
      maxLength: maxLength(100),
      validFormat: val => /^\d{6}$/.test(val)
    },
    contry: {
      required,
      maxLength: maxLength(100),
      alpha: val => /^[а-яё]*$/i.test(val)
    },
    stateContry: {
      required,
      maxLength: maxLength(100),
      alpha: val => /^[а-яё]*$/i.test(val)
    },
    city: {
      required,
      maxLength: maxLength(100),
      alpha: val => /^[а-яё]*$/i.test(val)
    },
    street: {
      required,
      maxLength: maxLength(100),
      alpha: val => /^[а-яё]*$/i.test(val)
    },
    house: {
      required,
      maxLength: maxLength(100),
      alpha: val => /^[а-яё]*$/i.test(val)
    },
    selectedDoc: {
      required
    },
    passportIssued: {
      required,
      maxLength: maxLength(100),
      alpha: val => /^[а-яё]*$/i.test(val)
    },
    passportIssuedDate: {
      required,
      validFormat: val => /^([1-31]{2}\s{1}[1-12]{2}\s{1}[1900-2020]{4})?$/.test(val)
    }
  },

  methods: {
    someAction () {
      alert('Новый клиент успешно создан')
    }
  }

}

</script>

<style scoped>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.form-group {
  display: block;
  width: 30%;
  margin: 0 auto;
  margin-bottom: 20px;
  text-align: left;
}

.form-group input {
  width: 100%;
  height: 30px;
  padding: 5px;
}
.form-group .error {
  color: red;
  font-size: 12px;
}
 .checkbox-group-checkbox{
  display: block;
  width: 50%;
  margin: 0 auto;
  margin-bottom: 20px;
  text-align:  center;
 }
button {
  width: 200px;
  height: 50px;
  background-color: #3311cc;
  color: white;
  padding: 15px;
  font-size: 16px;
  position: relative;
  left: 50%;
  transform: translate(-50%, 0);
}
.text {
    text-align:  center;
   }

</style>
