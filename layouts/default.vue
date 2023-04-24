<template>
  <div>
    <div class="body-t">
      <Head>
        <!-- Bootstrap CSS -->
        <!-- <link
        href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css"
        rel="stylesheet"
        integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC"
        crossorigin="anonymous"
      /> -->
      </Head>

      <TheMenu />
      <slot></slot>
    </div>
    <div class="p-3 bg-success bg-gradient text-white text-center footer">
      Демо сайт создан
      <a href="https://php-cat.com" class="text-white" target="_blank">
        Сергеем Баклановым
      </a>
    </div>
  </div>
</template>

<script>
// import { defineComponent } from '@vue/composition-api'

// export default defineComponent({
//     setup() {

//     },
// })
</script>

<style scoped>
.body-t {
  min-height: 90vh;
}
</style>
