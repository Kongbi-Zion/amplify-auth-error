<template>
  <button class="button" @click="federatedGoogleSignup">
    SignIn with google
    <NuxtLink to="/content/tttttttttttt">Move</NuxtLink>
  </button>
</template>

<script>
import { Auth } from "aws-amplify";
import { CognitoHostedUIIdentityProvider } from "@aws-amplify/auth/lib/types";
export default {
  name: "HomePage",
  methods: {
    async federatedGoogleSignup() {
      try {
        Auth.federatedSignIn({
          provider: CognitoHostedUIIdentityProvider.Google,
        });
      } catch (err) {
        console.log(`Signup Error ${err.message}`);
      }
    },
  },
};
</script>

<style lang="css" scoped>
.button {
  margin: 5rem 4rem;
}
.button:hover {
  cursor: pointer;
}
</style>
