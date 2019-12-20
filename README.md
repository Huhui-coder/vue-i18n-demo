借助vue-i18n 完成语言国际化需求。

判断本地存储是否存在语言配置，如果不存在，将设置默认的语言配置为'zh'，并将配置保存到本地，这样每次打开都是上次配置好的语言环境了。

如果你的项目中存在，需要下拉框渲染的数据而同时需要语言国际化。

```
<el-select v-model="value" :placeholder="$t('i18nView.selectPlaceholder')">
            <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
            />
          </el-select>
```

那么，我们就需要在每一次设置完语言环境后，重新渲染一次options数据。

```
watch: {
    lang() {
      this.setOptions()
    }
  },
```

```
methods: {
    setOptions() {
      this.options = [
        {
          value: '1',
          label: this.$t('i18nView.one')
        },
        {
          value: '2',
          label: this.$t('i18nView.two')
        },
        {
          value: '3',
          label: this.$t('i18nView.three')
        }
      ]
    }
  }
```

安装依赖：

```
npm i 
```

运行：

```
npm run dev
```

