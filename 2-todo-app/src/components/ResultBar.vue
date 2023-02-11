<template>
  <small v-if="itemCount > 0" class="mt-2 d-flex justify-content-end green">Have {{ itemCount }} todos </small>
  <small v-else class="mt-2 d-flex justify-content-end green">Empty todo list </small>
</template>

<script>
export default {
  props: ["itemCount"],
};
</script>
