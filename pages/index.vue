<template>
  <button @click="showMessageFromBackend">Show message from backend {{message}}</button>
</template>

<script>
export default {
  data() {
    return { message: '' }
  },
  methods: {
    async showMessageFromBackend () {
      this.message = '';
      try {
        const response = await this.$axios.get('/api/test');
        this.message = response.data;
      } catch (err) {
        this.message = 'error';
        console.log(err)
      }
    }
  }
}
</script>