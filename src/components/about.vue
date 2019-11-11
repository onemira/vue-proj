<template>
  <div class="about">
    <h1>Hello {{ their_name }}, this is an about page</h1>
    <p>Lorem Ipsum</p>
  </div>
</template>

<script>
export default {
  name: "skills",
  data() {
    return {
      their_name: this.$route.params.name
    };
  }
};
</script>