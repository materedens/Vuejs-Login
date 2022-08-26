<template>
  <div>
    <b-container>
      <b-row align-h="center" class="mt-5">
        <b-col cols="5">
          <b-card class="p-3">
            <h3 class="mb-4">LogIn</h3>
            <b-form @submit="onSubmit" @reset="onReset" v-if="show">
              <b-form-group id="input-group-1" label="Email address:" label-for="input-1">
                <b-form-input id="input-1" v-model="form.email" type="email" placeholder="Enter email" required>
                </b-form-input>
              </b-form-group>&nbsp;

              <b-form-group id="input-group-2" label="Password:" label-for="input-2">
                <b-form-input id="input-2" v-model="form.password" type="password" placeholder="Enter Password"
                  required></b-form-input>
              </b-form-group>&nbsp;

              <b-form-group id="input-group-4" v-slot="{ ariaDescribedby }">
                <b-form-checkbox-group v-model="form.checked" id="checkboxes-4" :aria-describedby="ariaDescribedby">
                  <b-form-checkbox value="remember"> &nbsp;Remember Me</b-form-checkbox>
                </b-form-checkbox-group>
              </b-form-group>
              <div class="d-flex justify-content-between">
                <div>
                  <b-button type="submit" variant="primary">Submit</b-button>&nbsp;
                  <b-button type="reset" variant="danger">Reset</b-button>
                </div>
                <div>
                  <a href="#" v-b-modal.modal1>Forgot Password</a>
                </div>
              </div>
            </b-form>
          </b-card>
        </b-col>
      </b-row>
    </b-container>
    <b-modal id="modal1" title="Forgot Password">
      <b-form-group id="input-group-3" label="Password:" label-for="input-3">
        <b-form-input id="input-3" v-model="form.password" type="password" placeholder="Enter Password" required>
        </b-form-input>
      </b-form-group>&nbsp;
      <div class="d-flex justify-content-between">
        <div>
          <b-button type="submit" variant="primary">Submit</b-button>
        </div>
      </div>
    </b-modal>
  </div>
</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Lato:400,700');

body {
  background: #ffffff !important;
  font-family: 'Lato', sans-serif !important;
}
</style>
<script>
export default {
  data() {
    return {
      form: {
        email: '',
        name: '',
        food: null,
        checked: []
      },
      foods: [{ text: 'Select One', value: null }, 'Carrots', 'Beans', 'Tomatoes', 'Corn'],
      show: true
    }
  },
  methods: {
    onSubmit(event) {
      event.preventDefault()
      alert(JSON.stringify(this.form))
    },
    onReset(event) {
      event.preventDefault()
      // Reset our form values
      this.form.email = ''
      this.form.name = ''
      this.form.food = null
      this.form.checked = []
      // Trick to reset/clear native browser form validation state
      this.show = false
      this.$nextTick(() => {
        this.show = true
      })
    }
  }
}
</script>
