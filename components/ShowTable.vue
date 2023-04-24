<template>
  <div>
    <!-- loading: {{ loading }}    <br /> -->
    <!-- errored: {{ errored }}    <br /> -->
    <!-- data: {{ data.data }} -->
    <p>Последние 5 переводов</p>
    <table class="table table-striped">
      <thead>
        <tr>
          <th>Слово</th>
          <th>Перевод</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="w in data.data" :key="w">
          <td><nuxtLink :to="'api?q='+ w.word " >{{ capitalizeFirstLetter(w.word) }}</nuxtLink></td>
          <td>{{ capitalizeFirstLetter(w.translate) }}</td>
        </tr>
      </tbody>
    </table>

    <!-- <div v-if="errored && errored.length > 0" class="alert alert-warning">
      Упс: {{ errored }}
    </div>
    <div v-else-if="loading">
      ... Loading ...
    </div>
    <template v-else>
      <show-perevod-res></show-perevod-res>
    </template> -->
    <!-- </div> -->
    <!-- <br />
    <a href="#" @click.prevent="show7 = !show7">показать всю инфу</a>
    <div v-if="show7">
      <pre>res: {{ res }}
      </pre>
    </div> -->
  </div>
</template>

<script setup>

const props = defineProps({
  lang: {
    type: String,
    default: 'ru',
  },
})

import word from './use/word.js'
const {
  capitalizeFirstLetter
} = word()

let url = 'http://localhost/api/history?lang='+( props.lang ?? 'ru' )

const { data } = await useFetch(url, {
  // initialCache: true,
  method: 'GET',
  // body: { lang: props.lang },
})

console.log('show table', data ?? 'x')

</script>
