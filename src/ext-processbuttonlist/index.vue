<template>
  <div id="processBox" style="display: flex">
    <van-button
      v-for="(item, index) in actions"
      :key="index"
      :loading="loading"
      loading-type="spinner"
      type="info"
      native-type="button"
      @click="submit(item)"
      style="width: 100%; margin: 0px 2px"
      >{{ item }}</van-button
    >
  </div>
</template>

<script>

  export default {
    name: 'ExtProcessButtonList',
    props: ['value', 'title'],
    data() {
      return {};
    },
    inject: {
      spForm: {
        default: null,
      },
    },
    computed: {
      actions() {
        const acts = this.$route.meta.action || [];
        return acts;
      },

      actionStyle() {
        const len = actions().length;

        return {};
      },

      loading() {
        return this.value.loading == true;
      },
    },

    methods: {
      submit(act) {
        this.spForm.submit(act);
      },
    },
    mounted() {
      console.compProcess = this;
    },
  };
</script>

<style scoped></style>
