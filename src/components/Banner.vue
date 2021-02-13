<template>
  <section class="hero is-dark">
  <div class="hero-body">
    <p class="title">
      {{ title }}
    </p>
    <p class="subtitle mt-3">
        <slot></slot>
    </p>
  </div>
</section>
</template>

<script>
export default {
    name: 'Banner',

    props: {
        title: String,
    },
}
</script>

<style>

</style>