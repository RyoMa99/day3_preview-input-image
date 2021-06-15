<template>
  <div>
    <h1>{{ message }}</h1>
    <div>
      <input
        ref="preview"
        type="file"
        @change="uploadFile"
      >
    </div>
    <div
      v-if="url"
      style="position:relative"
    >
      <div
        style="position:absolute"
        @click="deletePreview"
      >
        X
      </div>
      <img :src="url">
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

@Component
export default class extends Vue {
  message = 'Try files'
  url = ''
  // https://stackoverflow.com/questions/46505813/vuejs-typescript-this-refs-reffield-value-does-not-exist
  $refs!: {
    preview: HTMLInputElement
  }

  uploadFile (): void {
    // こういうのをどうすればいいんだろうか
    // $refsにpreviewが絶対あることを定義し、nullはguard節をかます
    // const file = this.$refs.preview.files[0]
    // https://qiita.com/fufufukakaka/items/5d4a2f2272b8f1a4a16f
    if (this.$refs.preview.files === null) return
    console.log(this.$refs.preview)
    this.url = URL.createObjectURL(this.$refs.preview.files[0])
  }

  deletePreview (): void {
    this.url = ''
    this.$refs.preview.value = '' // 同じ画像を選んでもプレビューされるようにする
  }
}
</script>

<style scoped lang="scss">
</style>
