<template>
  <section class="container">
    <div class="columns is-multiline">
      <!-- v-for　でbreed_listからループ出力 -->
      <div v-for="(item, i) in breed_list" v-bind:key='i' class='column is-2'>
        <!-- <a class="button">{{ i }}</a> -->
        <nuxt-link :to="{ path: 'dogs/' + i}" class="button">{{ i }}</nuxt-link>
      </div>
    </div>
  </section>
</template>

<script>
import dogApi from '@/api/dog';
import {mapState} from 'vuex';

export default {
  async fetch ({store}) {
    let json = await dogApi.breeds()
    store.commit('breed_list_update', json) // ストアに保存。　storeのmutationsの名前と一致している
  },
  computed: mapState(['breed_list']), // mapState ヘルパーでstoreからデータを取り出す
}
</script>