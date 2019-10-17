# vue-ele-form-tree-select | vue-ele-form 的文件上传扩展组件

[![MIT Licence](https://badges.frapsoft.com/os/mit/mit.svg)](https://opensource.org/licenses/mit-license.php)
[![npm](https://img.shields.io/npm/v/vue-ele-form-tree-select.svg)](https://www.npmjs.com/package/vue-ele-form-tree-select)
[![download](https://img.shields.io/npm/dw/vue-ele-form-tree-select.svg)](https://npmcharts.com/compare/vue-ele-form-tree-select?minimal=true)

## 介绍

vue-ele-form-tree-select 做为 vue-ele-form 的第三方扩展, 通过对 [vue-treeselect](https://github.com/riophae/vue-treeselect) 的封装, 使得上传更加方便和容易

![image](https://raw.githubusercontent.com/dream2023/images/master/tree-select.ogpjyj1h8sj.gif)

## 安装

```bash
npm install vue-ele-form-tree-select --save
```

## 使用

```js
import EleForm from 'vue-ele-form'
import EleFormTreeSelect from 'vue-ele-form-tree-select'

// 注册 tree-select 组件
Vue.component('tree-select', EleFormTreeSelect)

// 注册 ele-form
Vue.use(EleForm, {
  // 专门设置全局的 tree-select 属性
  // 属性参考: https://vue-treeselect.js.org/
  'tree-select': {
    clearable: true // 所有的 tree-select 都会有 clearable = true的属性值
  }
})
```

```js
formDesc: {
  xxx: {
    label: 'xxx',
    // 只需要在这里指定为 tree-select 即可
    type: 'tree-select',
    // 属性参考: https://vue-treeselect.js.org/
    attrs: {
      multiple: true,
      clearable: true
    },
    options: [ {
      id: 'a',
      label: 'a',
      children: [ {
        id: 'aa',
        label: 'aa',
      }, {
        id: 'ab',
        label: 'ab',
      } ],
    }, {
      id: 'b',
      label: 'b',
    }, {
      id: 'c',
      label: 'c',
    } ]
  }
}
```

## 示例

```html
<template>
  <el-card
    header="ele-form-tree-select 演示"
    shadow="never"
    style="max-width: 1250px;min-height: 1000px;margin: 20px auto;"
  >
    <ele-form
      :form-data="formData"
      :form-desc="formDesc"
      :request-fn="handleRequest"
      @request-success="handleSuccess"
    />
  </el-card>
</template>

<script>
  export default {
    data() {
      return {
        formData: {
          location: null
        },
        formDesc: {
          location: {
            label: '地区',
            type: 'tree-select',
            attrs: {
              multiple: true,
              clearable: true,
              searchable: true
            },
            slots: {
              'before-list'(h) {
                return h('div', '这是插槽')
              }
            },
            options: [
              {
                id: 'fruits',
                label: 'Fruits',
                children: [
                  {
                    id: 'apple',
                    label: 'Apple 🍎',
                    isNew: true
                  },
                  {
                    id: 'grapes',
                    label: 'Grapes 🍇'
                  },
                  {
                    id: 'pear',
                    label: 'Pear 🍐'
                  },
                  {
                    id: 'strawberry',
                    label: 'Strawberry 🍓'
                  },
                  {
                    id: 'watermelon',
                    label: 'Watermelon 🍉'
                  }
                ]
              },
              {
                id: 'vegetables',
                label: 'Vegetables',
                children: [
                  {
                    id: 'corn',
                    label: 'Corn 🌽'
                  },
                  {
                    id: 'carrot',
                    label: 'Carrot 🥕'
                  },
                  {
                    id: 'eggplant',
                    label: 'Eggplant 🍆'
                  },
                  {
                    id: 'tomato',
                    label: 'Tomato 🍅'
                  }
                ]
              }
            ]
          }
        }
      }
    },
    methods: {
      handleRequest(data) {
        console.log(data)
        return Promise.resolve()
      },
      handleSuccess() {
        this.$message.success('提交成功')
      }
    },
    mounted() {}
  }
</script>

<style>
  body {
    background-color: #f0f2f5;
  }
</style>
```

## 相关链接

- [vue-treeselect](https://vue-treeselect.js.org/)
- [vue-ele-form](https://github.com/dream2023/vue-ele-form)
- [element-ui](http://element-cn.eleme.io)
