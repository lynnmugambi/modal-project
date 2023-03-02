<template>
  <div class="backdrop" @click.self="closeModal">
    <div class="modal" :class="{ sale: theme === 'sale' }">
      <slot> Default content that shows incase nothing is passed in the slot</slot>
      <div class="actions">
        <slot name="links"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['theme'],
  methods: {
    closeModal() {
      this.$emit('close')
    }
  }
}

/* Components make code reusable, customizable. Props help to create a single source of truth. */

</script>

<style> /* You can use scoped css here to lock in the css variables, although consider this affects perfomance if you do it alot, it is minimal.
The alternative is to use css specifiers that are unique to the component so even without the scoped keyword, it wont clash */
 .modal {
   width: 400px;
   padding: 20px;
   margin: 100px auto;
   background: white;
   border-radius: 10px;
 }

 .modal .actions {
   text-align: center;
   margin: 30px 0;
 }

 .modal .actions a {
   color: darkgray;
   padding: 10px;
   border: 1px solid darkgray;
   border-radius: 5px;
   text-decoration: none;
   margin: 10px;
 }

 .modal.sale {
   background: red;
   color: white;
 }

 .modal.sale h1 {
   color: white;
 }

 .modal.sale .actions a {
   color: white;
   border: 1px solid white;

 }

 .modal h1 {
   color: blue;
 }

 .backdrop {
   top: 0;
   position: fixed;
   background: rgba(0, 0, 0, 0.5);
   width: 100%;
   height: 100%;
 }
</style>