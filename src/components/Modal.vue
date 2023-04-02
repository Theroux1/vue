<script setup>

defineProps({
  show: Boolean
});

</script>

<template>
  <Transition
      enter-from-class="opacity-0 scale-125"
      enter-to-class="opacity-100 scale-100"
      enter-active-class="transition duration-300"
      leave-active-class="transition duration-200"
      leave-from-class="opacity-100 scale-100"
      leave-to-class="opacity-0 scale-125"
  >
    <div v-if="show" class="modal-mask">
      <div class="modal-container">
        <div>
          <slot>default body</slot>
        </div>

        <footer class="modal-footer">
          <slot name="footer">
            <button @click="$emit('close')">Close</button>
          </slot>
        </footer>
      </div>
    </div>
  </Transition>
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