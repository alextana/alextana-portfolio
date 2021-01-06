<template>
  <button
    class="btn-primary font-bold text-black my-3 py-2 px-4 rounded-full focus:outline-none"
  >
    <slot></slot>
  </button>
</template>

<script>
export default {};
</script>

<style>
.btn-primary {
  transition: 0.2s ease;
  background: #27fb6b;
}
.btn-primary:hover {
  background: #fff;
}
</style>