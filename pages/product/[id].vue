<script setup >
const route = useRoute()

</script>

<template>
  <div>
    Page: product/id:{{ route.params.id }}
  </div>
</template>

<style scoped></style>
