<template>
  <div style="width: 100%">
    <van-field
      readonly
      clickable
      :name="name"
      :value="fieldValue"
      :label="labelText"
      :placeholder="placeholder"
      @click="showCalendar = true"
      :rules="rules"
    >
      <template #label>
        <span>{{ labelText }}</span>
        <span class="require" v-if="required == 'true' || required == true">*</span>
      </template>
    </van-field>
    <van-calendar :poppable="true" v-model="showCalendar" @confirm="onConfirm" />
  </div>
</template>

<script>
  import { formatToDate } from '../utils/dateUtils';

  export default {
    name: 'ExtDate',
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
        default: '日期',
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
        showCalendar: false,
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
    methods: {
      onConfirm(date) {
        this.fieldValue = formatToDate(date);
        this.showCalendar = false;
      },
    },
  };
</script>

<style lang="" scoped></style>
