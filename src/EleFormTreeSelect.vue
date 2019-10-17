<template>
  <treeselect
    :class="desc.class"
    :options="options"
    :style="desc.style"
    class="ele-form-tree-select"
    v-bind="attrs"
    v-model="newValue"
    v-on="onEvents"
  >
    <template v-for="(render, key) of desc.slots" v-slot:[key]="data">
      <extend-slot :data="data" :key="key" :render="render" />
    </template>
  </treeselect>
</template>

<script>
import Treeselect from '@riophae/vue-treeselect'
import '@riophae/vue-treeselect/dist/vue-treeselect.css'
import formMixin from 'vue-ele-form/lib/mixins/formMixin'

export default {
  name: 'EleFormTreeSelect',
  mixins: [formMixin],
  components: { Treeselect },
  data () {
    return {
      defaultAttrs: {
        placeholder: '请选择' + this.desc.label
      }
    }
  }
}
</script>

<style>
.vue-treeselect {
  line-height: 20px;
  color: #606266;
}

.vue-treeselect__input {
  -webkit-appearance: none;
  background-image: none;
  border-radius: 4px;
  display: block;
  box-sizing: border-box;
  color: #606266;
  display: inline-block;
  outline: none;
}
.vue-treeselect__label {
  font-size: 14px;
  padding: 0 20px;
  position: relative;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  color: #606266;
  height: 34px;
  line-height: 34px;
  box-sizing: border-box;
  cursor: pointer;
}

.vue-treeselect__option--selected .vue-treeselect__label {
  color: #409eff;
}
</style>
