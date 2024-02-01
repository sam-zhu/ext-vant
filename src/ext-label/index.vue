<template>
  <div class="rowFlex">
    <div class="colTitle">{{ labelText }}</div>
    <div class="colValue">{{ value }}</div>
  </div>
</template>

<script>

  export default ({
    name: 'ExtLabel',
    props: {
      title: {
        default: null,
      },
      value: {
        default: null,
      },
    },
    data() {
      return {};
    },

    computed: {
      labelText: function () {
        return `${this.title}：`;
      },
    },
    methods: {},
  });
</script>

<style scoped></style>
