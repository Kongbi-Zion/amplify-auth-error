<template>
    <div>
        {{ user }}
    </div>

    <button class="button" @click="signOut">signout</button>
</template>

<script>
    import { Auth, Hub } from "aws-amplify";
    export default {
        name: 'AuthPage',
        data(){
            return {
                user: "Loading..."
            }
        },
        async mounted(){
            Hub.listen('auth', async (data) => { 
                if(data.payload.event === 'signIn') {
                    const user = await Auth.currentAuthenticatedUser();
                    this.user = user.attributes;
                }
            })
        },
        methods: {
            async signOut() {
                try{
                    Auth.signOut();
                }catch(error){
                    console.log("error:", error);
                }
            },
        }
    }
</script>
<style lang="css">
    .button{
        margin-top: 5rem;
    }
    .button:hover{
        cursor: pointer;
    }
</style>