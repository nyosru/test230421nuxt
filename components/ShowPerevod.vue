<template>
  <div>
    <!-- loading: {{ loading }}    <br /> -->
    <!-- errored: {{ errored }}    <br /> -->

    <div v-if="errored && errored.length > 0" class="alert alert-warning">
      Упс: {{ errored }}
    </div>
    <div v-else-if="loading">
      ... Loading ...
    </div>
    <template v-else>
      <show-perevod-res></show-perevod-res>
    </template>
    <!-- </div> -->
    <br />
    <a href="#" @click.prevent="show7 = !show7">показать всю инфу</a>
    <div v-if="show7">
      <pre>res: {{ res }}
      </pre>
    </div>
  </div>
</template>

<script setup>


const props = defineProps({
  lang: {
    type: String,
    default: 'ru',
  },
})

import oxford from './use/oxford.js'

const {
  //
  word,
  loading,
  errored,
  res,
} = oxford()

const show7 = ref(false)

errored.value = false

const getTranslation = async ( toLang = 'ru' , wordOrigin = '') => {
  console.log('getTranslationRu word', wordOrigin)

  errored.value = false

  //   word.value = wordOrigin
  res.value = {}

  loading.value = true

  let datar = {
    word: word.value,
    fromLang: 'en',
    toLang: toLang,
  }

  let url = 'http://localhost/api/translate'

  // const { pending, data: items } = useLazyFetch(url, {
  //   method: 'POST',
  //   body: datar,
  // })

  const { pending, data } = await useFetch(url, {
    initialCache: true,
    method: 'POST',
    body: datar,
  })

  console.log('getTranslationRu pending', pending)

  console.log('getTranslationRu data', data)
  console.log('getTranslationRu data2', data.value)
  console.log('getTranslationRu data3', data.value.data)

  res.value = data.value.data

  console.log('getTranslationRu res', res.value)

  //   console.log('------56------')
  //   console.log('getTranslationRu', items)

  if (res.value.info.http_code == 429) {
    errored.value = 'Usage limit exceeded.'
    console.log(11)
  } else if ( res.value.error && res.value.error != '') {
    errored.value = res.value.error
    console.log(112 , res.value.error)
  } else {
    loading.value = false
    console.log(113)
  }

  // console.log('------72------')
  // console.log('items', items)

  // res.value = items
  // } catch (error) {
  //   console.log('------76------')
  //   console.log(error)
  // }
}

// const getTranslation = async (wordOrigin = '') => {

//   try {
//     const response = await fetch(
//       `https://od-api.oxforddictionaries.com/api/v2/translations/es/en/` +
//         wordOrigin,
//       {
//         method: 'GET',
//         headers: {
//           app_id: '1e0f6373',
//           app_key: '6da9adfd84b6b43a9024d0d58856373e',
//         },
//       },
//     )
//     const data = await response.json()
//   } catch (error) {
//     console.error(error)
//   }
// }

const route = useRoute()
const oldWord = ref('')

// слово для перевода изменилась
watchEffect(() => {
  if ( route.query.q && route.query.q.length > 0 && oldWord.value != route.query.q) {
    oldWord.value = route.query.q
    getTranslation( props.lang, route.query.q)
  }
})

// getTranslationRu(route.query.word)
</script>
