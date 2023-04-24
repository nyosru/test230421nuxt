<template>
  <div>
    <!-- prop lang: {{ lang ?? '11' }}     <br/> -->
    <!-- <div v-if="typeof(q) !== 'undefined' ">word: {{ q ?? 'x' }} </div> -->
    
    <h3>Перевод по оксфордски</h3>
    <!-- en > sp12345 -->
    <br />
    <!-- <form @submit.prevent="getTranslationRu(word)"> -->
    <form @submit.prevent="refresh">
      <div class="input-group mb-3">
        <input
          type="text"
          v-model="word2"
          required
          class="form-control"
          placeholder="Слово en для перевода"
          aria-label="Слово en для перевода"
          aria-describedby="button-addon2"
        />
        <button
          class="btn btn-info xbtn-outline-secondary"
          type="submit"
          id="button-addon2"
        >
          Перевести
        </button>
      </div>

      <!-- <form> -->
      <!-- <div class="mb-3">
        <label for="exampleInputEmail1" class="form-label">
          Слово en для перевода:
        </label>
        <input
          type="text"
          class="form-control"
          id="exampleInputEmail1"
          v-model="word"
          required
        />
        <div id="emailHelp" class="form-text">
          Мы никогда никому не передадим ваш запрос.
        </div>
      </div> -->
      <!-- <div class="mb-3">
    <label for="exampleInputPassword1" class="form-label">Пароль</label>
    <input type="password" class="form-control" id="exampleInputPassword1">
  </div> -->
      <!-- <div class="mb-3 form-check">
    <input type="checkbox" class="form-check-input" id="exampleCheck1">
    <label class="form-check-label" for="exampleCheck1">Проверить меня</label>
  </div> -->
      <!-- <button type="submit" class="btn btn-primary">Перевести</button> -->
      <!-- </form> -->

      <!-- Слово en для перевода: -->
      <!-- <input v-model="word" required /> -->
      <!-- <br /> -->
      <!-- <button type="submit">Перевести</button> -->
    </form>
    <!-- <br />
    <br /> -->
    <!-- word: {{ word }} -->
    <!-- <br /> -->
    <!-- count: {{ count }} -->
    <!-- <br /> -->
    <!-- count2: {{ count2 }} -->
    <br />
    <!-- translation: {{ translation }} -->
  </div>
</template>

<script setup>

const props = defineProps({
  lang: {
    type: String,
    default: 'ru',
  },
})

const word2 = ref('')

import oxford from './use/oxford.js'
const { word } = oxford()

const router = useRouter()

const refresh = () => {
  word.value = word2.value
  router.push({ path: '/'+props.lang+'/api', query: { q: word.value } })
}

</script>
