# day3

[画像のプレビューを出してみる](https://reffect.co.jp/vue/input-image-previes-vue-js)

## 学んだこと
- `this.$refs.preview.files[0]`
  - このコードはpreviewがundefinedの可能性があることとfilesがnullの可能性があることの2つの警告がだされる
    - 対処法
    - refsにpreviewが絶対存在することを定義する
      ```js
        $refs!: {
          preview: HTMLInputElement
        }
      ```
    - guard節を使ってnullを除外する
      ```js
        if (this.$refs.preview.files === null) return
        this.url = URL.createObjectURL(this.$refs.preview.files[0])
      ```

## Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn serve
```

### Compiles and minifies for production
```
yarn build
```

### Run your unit tests
```
yarn test:unit
```

### Lints and fixes files
```
yarn lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
