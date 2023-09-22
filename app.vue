<template>
  <div>
    <NuxtPage />
  </div>
</template>
<script>
import { Auth } from "aws-amplify";
export default {
  async mounted() {
    const user = await Auth.currentAuthenticatedUser();
    console.log("user : ", user);
  },
};
</script>
