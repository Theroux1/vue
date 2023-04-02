<script setup>

defineProps({
  show: Boolean
});

</script>

<template>
  <div class="modal-mask" v-if="show">
    <div class="modal-container">

<!--      <header>-->
<!--        <slot name="header">-->
<!--          default header-->
<!--        </slot>-->
<!--      </header>-->
      <div>
        <slot>default body</slot>
      </div>
      <footer class="border-t-2 pt-2">
        <slot name="footer">
          default footer
        </slot>
        <button class="block bg-green-400 rounded p-3 text-white" @click="$emit('close')">Close</button>
      </footer>
    </div>
  </div>
</template>

<style>
.modal-mask {
  position: fixed;
  inset: 0;
  background: rgb(0 0 0 / 66%);

  display: grid;
  place-items: center;
}

.modal-container {
  background: #fff;
  padding: 1rem;
  width: 80vw;
  max-width: 500px;
  border-radius: 12px;
}
</style>