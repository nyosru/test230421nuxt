<template>
  <div>
    <Head>
      <title>ru lang</title>
    </Head>

    <div class="container">
      <div class="row mb-5 mt-3">
        <div class="col-12 text-center bg-info" style="border-radius: 5px;">
          <h2>Перевод с english на испанский</h2>
        </div>

        <div class="col-12 col-sm-8 col-lg-6 text-center">
          <show-table lang="es"></show-table>
        </div>

        <br />
        <br />

        <div
          class="col-12 text-center"
          style="background-color: #ffeeee; border-radius: 20px;"
        >
          <h2>Перевод с english on испанский</h2>
        </div>
        <div class="col-12 col-md-6">
          <the-perevod lang="es"></the-perevod>
        </div>
        
      </div>
    </div>
  </div>
</template>

<script setup>
// const router = useRouter();
// router.push({ path: '/translate' })
</script>
