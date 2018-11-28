<template>
    <div class="about">
    <h1>This is an about page</h1>
    <p>Hello {{their_name}} - About page</p>
    </div>
</template>

<script>
export default {
  data() {
    return {
        your_name : this.$route.params.name
    }
  },
}
</script>
