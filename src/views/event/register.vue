/* eslint-disable prettier/prettier */
<template>
  <p>Register for the event here please</p>
  <button @click="register">Register me</button>
</template>
<script>
export default {
  props: ['event'],
  inject: ['GStore'],
  methods: {
    register() {
      this.GStore.flashMessage =
        'You are successfully registered for' + this.event.title;
      setTimeout(() => {
        //after 3 second delete the message
        this.GStore.flashMessage = '';
      }, 3000);
      this.$router.push({
        name: 'EventDetails',
        params: { id: this.event.id },
      });
    },
  },
};
</script>
