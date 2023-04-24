<template>
  <div>
    <div
      class="alert alert-warning"
      v-if="res.message && res.message.length > 0"
    >
      <!-- 441 -->
      {{ res.message }}
    </div>
    <div
      class="alert alert-warning"
      v-if="res.error && res.error.length > 0"
    >
      <!-- 441 -->
      {{ res.error }}
    </div>
    <template v-else>
      <!-- 442 -->
      <h3>Как оксфорд переводит <u>{{ res.id }}</u></h3>
      <br />

      <!-- <pre> -->
      <!-- {{ da.value.data.results[0].lexicalEntries[0].entries[0].senses[0].translations[0].text }} -->
      <!-- {{ da.value.data.id }} -->
      <!-- </pre> -->

      <table
        class="table table-striped"
        v-if="
          res.results
        "
      >
        <thead>
          <tr>
            <td>Что</td>
            <td>Значение</td>
          </tr>
        </thead>
        <tbody>
          <template
            v-if="
              res.results[0].lexicalEntries[0].entries[0].senses[0]
                .translations &&
              res.results[0].lexicalEntries[0].entries[0].senses[0].translations
                .length > 0
            "
          >
            <tr
              v-for="i in res.results[0].lexicalEntries[0].entries[0].senses[0]
                .translations"
              :key="i.text"
            >
              <td>Перевод</td>
              <td>
                <div style="max-height: 100px; overflow: auto;">
                  {{ i.text }}
                </div>
              </td>
            </tr>
          </template>
          <tr
            v-else-if="
              res.results[0].lexicalEntries[0].entries[0].senses[0]
                .translations[0].text
            "
          >
            <td>Перевод</td>
            <td>
              <div style="max-height: 100px; overflow: auto;">
                {{
                  res.results[0].lexicalEntries[0].entries[0].senses[0]
                    .translations[0].text
                }}
              </div>
            </td>
          </tr>

          <tr
            v-for="v in res.results[0].lexicalEntries[0].entries[0].senses[0]
              .examples"
            :key="v"
          >
            <td>Пример использования</td>
            <td>
              {{ capitalizeFirstLetter(v.text) }}
              <br />
              {{ v.translations[0].text }}
            </td>
          </tr>

          <!-- произношение оригинала -->

          <tr
            v-for="v in res.results[0].lexicalEntries[0].entries[0]
              .pronunciations"
            :key="v"
          >
            <td>Как звучит оригинал</td>
            <td>
              {{ v.dialects[0] }}
              <br />
              <a :href="v.audioFile" target="_blank">{{ v.audioFile }}</a>
            </td>
          </tr>
        </tbody>
      </table>

      <div v-else class="alert alert-warning p-3">
        Упс ... перевода этот словарь не знает
        <br />
        Ошибка 47
      </div>
    </template>
  </div>
</template>

<script setup>
import word from './use/word.js'
const {
  capitalizeFirstLetter
} = word()

import oxford from './use/oxford.js'
const {
  // word,
  // loading,
  // errored,
  res,
} = oxford()
</script>
