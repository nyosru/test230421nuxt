<template>
  <div>
    <Head>
      <title>en > es api lang</title>
    </Head>
    <div class="container">

      <div class="row mb-5 mt-3">
        <div
          class="col-12 text-center"
          style="background-color: #ffeeee; border-radius: 20px;"
        >
          <h2>Перевод en на Испанский api page</h2>
        </div>
      </div>

      <div class="row">
        <div class="col-6">
          <the-perevod lang="es" ></the-perevod>
        </div>
        <div class="col-6">
          <show-perevod lang="es" ></show-perevod>
        </div>
      </div>

    </div>
  </div>
</template>

<script setup>

// import oxford from './../../components/use/oxford.js'
// const { word } = oxford()

// // const router = useRouter();
// // router.push({ path: '/translate' })

// const route = useRoute()
// let ww = route.query.word
// // When accessing /posts/1, route.params.id will be 1
// console.log(route.params.word)

</script>