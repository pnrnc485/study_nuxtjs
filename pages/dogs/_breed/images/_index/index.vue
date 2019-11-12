<template>
    <div align="center">
        <!--　stateのdog_listから画像のURLを取得して表示 -->
        <img :src="dog_list[$route.params.index].url" :class="centering_parent">
    </div>
</template>

<script>
import {mapState} from 'vuex'; // storeからデータを取り出すためのヘルパー

export default {
    computed: mapState(['dog_list']),
}
</script>