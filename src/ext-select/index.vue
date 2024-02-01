<template>
  <div style="width: 100%">
    <van-field
      readonly
      clickable
      :name="name"
      :value="fieldText"
      :label="labelText"
      :placeholder="placeholder"
      @click="showPicker = true"
      :rules="rules"
    >
      <template #label>
        <span>{{ labelText }}</span>
        <span class="require" v-if="required == 'true' || required == true">*</span>
      </template>
    </van-field>
    <van-popup v-model="showPicker" position="bottom">
      <van-picker
        show-toolbar
        :columns="columnOptions"
        @confirm="onConfirm"
        @cancel="showPicker = false"
      />
    </van-popup>
  </div>
</template>

<script>

  export default ({
    name: 'ExtSelect',
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
      columns: {
        type: Array,
        default: function () {
          return [];
        },
      },
      //自定义
      fieldNames: {
        type: Object,
        default: function () {
          return {};
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
      return {
        showPicker: false,
        // fieldText: '',
        selectItem: {},
      };
    },
    computed: {
      placeholder: function () {
        return `${this.label}`;
      },

      labelText: function () {
        return `${this.label}：`;
      },

      columnOptions: function () {
        const labelfield = this.fieldNames.label || 'text';
        const valfiled = this.fieldNames.value || 'value';
        const cols = this.columns.map((m) => {
          return {
            text: m[labelfield],
            value: m[valfiled],
            data: m,
          };
        });

        return cols;
      },

      fieldText: {
        get() {
          if (this.value) {
            const opts = this.columnOptions;
            const selOpt = opts.find((m) => m.value === this.value);
            if (selOpt) return selOpt.text;
            return null;
          }
        },
        set(val) {},
      },
    },

    watch: {},
    methods: {
      onConfirm(val) {
        this.fieldText = val.text;
        this.$emit('input', val.value);
        this.$emit('change', val);
        this.showPicker = false;
      },
    },
  });
</script>

<style lang="" scoped></style>
