<template>
  <h1>{{ title }}</h1>
  <p>Welcome...</p>
  <teleport to=".modals" v-if="showModal">
    <!-- <Modal :header="header" :text="text" theme="sale" @close="toggleModal"/> -->
    <Modal theme="sale" @close="toggleModal">
      <!-- <h1>Ninja Giveaway!</h1>
      <p>Grab your Ninja swag for half price!</p> -->

      <template v-slot:named>
        <a href="#">Sign Up</a>
        <a href="#">More Info</a>
      </template>
      <h1>{{ header }}</h1>
      <p>{{ text }}</p>

    </Modal>
  </teleport>
  <button @click="toggleModal">Open Modal</button>

  <teleport to=".modals" v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <template v-slot:named>
        <u>
          <li>My Modal</li>
          <li>My Modal two</li>
          <li>My Modal three</li>
        </u>
      </template>

      <h1>My Modal Two</h1>
      <p>Modal Content</p>
    </Modal>
  </teleport>
  <button @click="toggleModalTwo">Open Modal Two</button>

</template>

<script>

  import Modal from './components/Modal-component.vue'
  export default {
    name: 'App',
    components: {Modal},
    data() {
      return {
        title: 'My First Vue App :)',
        header: 'Ninja Giveaway!',
        text: 'Grab your Ninja swag for half price!',
        showModal: false,
        showModalTwo: false
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
#app, .modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
