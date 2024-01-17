<template>
  <div style="width: 100%">
    <van-field
      v-model="fieldValue"
      :name="name"
      :label="labelText"
      :placeholder="placeholder"
      :type="type"
      rows="3"
      :maxlength="maxlength"
      :readonly="readonly"
      :rules="rules"
    />
  </div>
</template>

<script>
  import Vue from 'vue';

  export default Vue.extend({
    name: 'ExtComment',
    props: {
      value: {
        type: String,
        default: null,
      },
      name: {
        type: String,
        default: 'NULL',
      },
      label: {
        type: String,
        default: '审核意见',
      },
      type: {
        type: String,
        default: 'textarea',
      },
      maxlength: {
        type: Number | String,
        default: 200,
      },
      readonly: {
        type: Boolean,
        default: false,
      },
      rules: {
        type: Array,
        default: function () {
          return [];
        },
      },
    },
    data() {
      return {};
    },
    computed: {
      placeholder: function () {
        return `请输入${this.label}`;
      },
      fieldValue: {
        get() {
          return this.value;
        },
        set(val) {
          this.$emit('input', val);
        },
      },

      labelText: function () {
        return `${this.label}：`;
      },
    },
    methods: {},
  });
</script>

<style lang="" scoped></style>
