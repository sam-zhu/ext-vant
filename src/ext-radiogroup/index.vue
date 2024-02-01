<template>
  <div style="width: 100%">
    <van-field v-model="fieldValue" :name="name" :label="labelText" :rules="rules">
      <template #input>
        <van-radio-group v-model="fieldValue" direction="horizontal">
          <van-radio v-for="item in options" :key="item.value" :name="item.value">
            {{ item.label }}
          </van-radio>
        </van-radio-group>
      </template>
      <template #label>
        <span>{{ labelText }}</span>
        <span class="require" v-if="required == 'true' || required == true">*</span>
      </template>
    </van-field>
  </div>
</template>

<script>

  // const options = [
  //   { label: 'Apple', value: 'Apple' },
  //   { label: 'Pear', value: 'Pear' },
  //   { label: 'Orange', value: 'Orange' },
  // ];
  export default {
    name: 'ExtRadioGroup',
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
        default: '',
      },
      options: {
        type: Array,
        default: function () {
          return [];
        },
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
      return {};
    },
    computed: {
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
  };
</script>

<style lang="" scoped></style>
