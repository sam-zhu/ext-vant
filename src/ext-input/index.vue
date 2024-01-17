<template>
  <div style="width: 100%">
    <van-field
      v-model="fieldValue"
      :name="name"
      :label="labelText"
      :placeholder="placeholder"
      :type="type"
      :rows="rows"
      :maxlength="maxlength"
      :readonly="readonly"
      :disabled="disabled"
      :rules="rules"
    >
      <template #label>
        <span>{{ labelText }}</span>
        <span class="require" v-if="required == 'true' || required == true">*</span>
      </template>
    </van-field>
  </div>
</template>

<script>
  import Vue from 'vue';

  export default Vue.extend({
    name: 'ExtInput',
    props: {
      value: {
        type: [String, Number],
        default: null,
      },
      name: {
        type: String,
        default: 'NULL',
      },
      label: {
        type: String,
        default: '',
      },
      type: {
        type: String,
        default: 'text',
      },
      rows: {
        type: Number,
        default: 1,
      },
      maxlength: {
        type: Number | String,
        default: 200,
      },
      readonly: {
        type: Boolean,
        default: false,
      },
      disabled: {
        type: Boolean,
        default: false,
      },
      required: {
        type: Boolean | String,
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
      return {
        // fieldValue: '',
      };
    },
    computed: {
      placeholder: function () {
        return `${this.label}`;
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
