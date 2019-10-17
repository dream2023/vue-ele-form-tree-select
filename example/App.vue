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
  data () {
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
            'before-list' (h) {
              return h('div', '这是插槽')
            }
          },
          options: [{
            id: 'fruits',
            label: 'Fruits',
            children: [{
              id: 'apple',
              label: 'Apple 🍎',
              isNew: true
            }, {
              id: 'grapes',
              label: 'Grapes 🍇'
            }, {
              id: 'pear',
              label: 'Pear 🍐'
            }, {
              id: 'strawberry',
              label: 'Strawberry 🍓'
            }, {
              id: 'watermelon',
              label: 'Watermelon 🍉'
            }]
          }, {
            id: 'vegetables',
            label: 'Vegetables',
            children: [{
              id: 'corn',
              label: 'Corn 🌽'
            }, {
              id: 'carrot',
              label: 'Carrot 🥕'
            }, {
              id: 'eggplant',
              label: 'Eggplant 🍆'
            }, {
              id: 'tomato',
              label: 'Tomato 🍅'
            }]
          }]
        }
      }
    }
  },
  methods: {
    handleRequest (data) {
      console.log(data)
      return Promise.resolve()
    },
    handleSuccess () {
      this.$message.success('提交成功')
    }
  },
  mounted () { }
}
</script>

<style>
body {
  background-color: #f0f2f5;
}
</style>
