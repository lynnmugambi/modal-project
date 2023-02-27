<template>
  <h1 class="example">{{ title }}</h1>
  <p>Welcome...</p>
  <div v-if="showModal">
    <Modal :title=modalTitle :text=modalText theme="sale" @close="showModal = false" />
  </div>
  <button @click.alt="toggleModal"> Show Modal (alt)</button>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: { Modal },
  data() {
    return {
      title: 'My First Vue3 App!',
      modalTitle: 'This is a title',
      modalText: 'This is a text',
      showModal: false,
    }
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1.example {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>