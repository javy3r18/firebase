<template>
  <div>
    <b-container>
      <b-form @submit.prevent="onSubmit">
      <b-form-group
        id="input-group-1"
        label="Email address:"
        label-for="input-1"
        description="We'll never share your email with anyone else."
      >
        <b-form-input
          id="input-1"
          v-model="form.email"
          type="email"
          placeholder="Enter email"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-2" label="Password:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="form.password"
          type="password"
          placeholder="Enter password"
          required
        ></b-form-input>
      </b-form-group>
      <b-button type="submit" variant="primary">Submit</b-button>
    </b-form>
    </b-container>
  </div>
</template>

<script>
export default {
  data(){
    return{
      form: {
        email: null,
        password: null
      }
    }
  },
  mounted(){
    console.log(this.$fire.auth);
  },

  methods: {
    async onSubmit(){
      try {
        await this.$fire.auth.createUserWithEmailAndPassword(this.form.email, this.form.password)
      }
      catch (e) {
        console.error(e)
      }
    }
  }

}
</script>
