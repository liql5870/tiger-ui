<demo>
一键打开 Dialog
</demo>
<template>
  <div>
    <Button @click="showDialog">打开对话框</Button>
  </div>
</template>
<script lang="ts">
export default {};
</script>
<script setup lang="ts">
import Button from "../../libs/Button.vue";
import { ref, h } from "vue";
import { openDialog } from "../../libs/openDialog";

const showDialog = () => {
  openDialog({
    title: h("strong", {}, "标题"),
    content: "你好",
    ok() {
      console.log("ok");
    },
    cancel() {
      console.log("cancel");
    },
  });
};
</script>
