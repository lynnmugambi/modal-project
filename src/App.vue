<template>
  <h1 class="example">{{ title }}</h1>
  <p>Welcome...</p>
  <div v-if="showModal">
    <Modal theme="sale" @close="showModal = false">
      <h1>This is a slot</h1>
      <p>This is some type of text</p>
      <template v-slot:links> <!-- Can be shortened to #links-->
        <a href="#">Sign Up</a>
        <a href="#">Sign In</a>
      </template>
    </Modal>
  </div>
  <div v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <template #links> <!-- Can be shortened to #links-->
        <a href="#">More Info</a>
      </template>
    </Modal>
  </div>
  <button @click.alt="toggleModal"> Show Modal (alt)</button>
  <button @click="toggleModalTwo"> Show Modal Two</button>
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
      showModalTwo: false,
    }
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
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
}

h1.example {
  text-decoration: underline;
  margin-bottom: .5rem;
}
</style>