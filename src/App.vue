<template>
  <div class="container" @submit.prevent="submitHandler">
    <form class="card">
      <h1>Bewerbung als VUE-Entwickler!</h1>

<!--      <div class="form-control" :class="{ invalid:errors.firstName }">-->
<!--        <label for="firstname">Geben Sie hier Ihren Vornamen ein.</label>-->
<!--        <input-->
<!--            type="text"-->
<!--            id="firstname"-->
<!--            placeholder="Vorname"-->
<!--            v-model.trim="firstName"-->
<!--        >-->
<!--        <small v-if="errors.firstName">{{ errors.firstName }}</small>-->
<!--      </div>-->

      <app-input
          my-placeholder="Vorname"
          label="Geben Sie hier Ihren Vornamen ein."
          :error="errors.firstName"
          v-model:value.trim="firstName"
      ></app-input>

<!--      <div class="form-control" :class="{ invalid:errors.lastName }">-->
<!--        <label for="lastname">Geben Sie hier Ihren Nachnamen ein.</label>-->
<!--        <input-->
<!--            type="text"-->
<!--            id="lastname"-->
<!--            placeholder="Nachname"-->
<!--            v-model.trim="lastName"-->
<!--        >-->
<!--        <small v-if="errors.lastName">{{ errors.lastName }}</small>-->
<!--      </div>-->

      <app-input
          my-placeholder="Nachname"
          label="Geben Sie hier Ihren Nachnamen ein."
          :error="errors.lastName"
          v-model:value.trim="lastName"
      ></app-input>

      <div class="form-control">
        <label for="age">Bitte geben Sie Ihr Alter an.</label>
        <input
            type="number"
            id="age"
            max="70"
            v-model.number="age"
        >
      </div>

      <div class="form-control">
        <label for="city">Wo wohnen Sie?</label>
        <select id="city" v-model="city">
          <option value="be">Berlin</option>
          <option value="hann">Hannover</option>
          <option value="hh">Hamburg</option>
          <option selected value="muc">München</option>
        </select>
      </div>

      <div class="form-checkbox">
        <span class="label">Sind Sie umzugsbereit?</span>
        <div class="checkbox">
          <label><input type="radio" name="trip" v-model="relocate" value="yes"/>Ja</label>
        </div>

        <div class="checkbox">
          <label><input type="radio" name="trip" v-model="relocate" value="no"/>Nein</label>
        </div>
      </div>

      <div class="form-checkbox">
        <span class="label"> Kenntnisse in Vue?</span>
        <div class="checkbox">
          <label><input type="checkbox" name="skills" v-model="skills" value="vuex"/> Vuex</label>
        </div>
        <div class="checkbox">
          <label><input type="checkbox" name="skills" v-model="skills" value="cli"/> Vue CLI</label>
        </div>
        <div class="checkbox">
          <label><input type="checkbox" name="skills" v-model="skills" value="router"/> Vue Router</label>
        </div>
      </div>

      <div class="form-checkbox">
        <span class="label">Datenschutzerklärung</span>
        <div class="checkbox">
          <label><input type="checkbox" name="agree" v-model="agree"/>Ich stimme AGB und Datenschutzerklärung zu</label>
        </div>
      </div>

      <button type="submit" class="btn primary">Senden</button>
    </form>
  </div>
</template>

<script>
import AppInput from "@/components/AppInput";
export default {
  components: {
    'app-input': AppInput
  },
  data(){
    return {
      firstName: '',
      lastName: '',
      age: 25,
      city: 'hann',
      relocate: null,
      skills: [],
      agree: false,
      errors: {
        firstName: null,
        lastName: null
  }
    }
  },
  methods: {
    formIsValid() {
      let isValid= true
      if(this.firstName.length === 0 ) {
        this.errors.firstName = ' Das Feld darf nicht leer sein.'
        isValid = false
      }
      if(this.lastName.length === 0) {
        this.errors.lastName = ' Das Feld darf nicht leer sein.'
        isValid = false
      }
      else {
        this.errors.firstName = null
        this.errors.lastName = null
      }
      return isValid
    },
    submitHandler(){
      if(this.formIsValid()) {
        console.group('Start-Data-Form')
        console.log('Vorname: ' + this.firstName)
        this.firstName = ''
        console.log('Nachname: ' + this.lastName)
        this.lastName = ''
        console.log('Age: ' + this.age)
        console.log('City: ' + this.city)
        console.log('Relocate: ' + this.relocate)
        console.log('Skills: ' + this.skills)
        console.log('Datenschutzerklärung: ' + this.agree)
        console.groupEnd('End-Data-Form')
      }
    }
  }
}
</script>

<style>
.form-control.invalid small {
  color: #e53935;
}
.form-control.invalid input {
  border-color: #e53935;
}
</style>
