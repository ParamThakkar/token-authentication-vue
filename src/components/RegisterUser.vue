<template>
  <div>
    <form
      autocomplete="nope"
      @submit.prevent="register"
    >
      <label for="name">Name:</label>
      <input
        v-model="name"
        type="text"
        name="name"
        autocomplete="nope"
        value
      >
      <label for="email">Email:</label>
      <input
        v-model="email"
        type="email"
        name="email"
        autocomplete="nope"
        value
      >
      <label for="password">Password:</label>
      <input
        v-model="password"
        type="password"
        name="password"
        autocomplete="nope"
        value
      >

      <button
        type="submit"
        name="button"
      >
        Register
      </button>

      <router-link :to="{name:'login'}">
        Already a user? Login here!
      </router-link>

    </form>
  </div>
</template>

<script>
export default {
  data () {
    return {
      name: '',
      email: '',
      password: ''
    }
  },
  methods: {
    register () {
      this.$store.dispatch('register', {
        name: this.name,
        email: this.email,
        password: this.password
      })
        .then(() => {
          this.$router.push({ name: 'dashboard' })
        })
    }
  }
}
</script>
