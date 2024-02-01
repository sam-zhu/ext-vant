<template>
  <div style="width: 100%">
    <van-nav-bar
      :title="title"
      left-text="返回"
      right-text=""
      left-arrow
      @click-left="onClickLeft"
    />
  </div>
</template>

<script>

  export default {
    name: 'ExtNav',
    props: {
      value: {
        type: Object,
        default: null,
      },
    },
    data() {
      return {
        showPicker: false,
      };
    },
    computed: {
      title: {
        get() {
          if (this.value) {
            return this.value.NodeName || this.$route.meta.title;
          }
          return this.$route.meta.title;
        },
      },
    },
    methods: {
      onClickLeft() {
        this.$router.back();
      },
    },
  };
</script>

<style lang="" scoped></style>
