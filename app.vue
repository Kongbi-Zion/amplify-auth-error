<template>
  <div>
    <NuxtPage />
  </div>
</template>
<script>
import { Auth } from "aws-amplify";
export default {
  mounted() {
    const user = Auth.currentAuthenticatedUser();
    console.log("user : ", user);
  },
};
</script>
