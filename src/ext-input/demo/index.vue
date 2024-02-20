<template>
  <demo-section>
    <demo-block title="基础用法">
        <ExtInput
            v-model="formModel.text"
            name="text"
            label="文本"
            placeholder="文本内容"
            maxlength="30"
            required="true"
            :rules="[{ required: true, message: '请填写文本内容' }]"
        />
        22
    </demo-block>
  </demo-section>
</template>
<script>
export default {
    name: 'ExtInputDemo',
    data(){
        return {
            formModel:{
                text:''
            }
        }
    }
}
</script>
