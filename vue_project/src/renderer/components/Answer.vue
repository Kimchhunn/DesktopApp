<template>
    <div id="login-form">
        <p1>This is answer component</p1>
        <button type="button" v-on:click="changeQuestion(1)">1</button>
        <div v-for="item in items" :key="item.id">
            <v-btn outline color="indigo" v-on:click="changeQuestion(1)">{{ item.question_number }}</v-btn>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Login',
        data () {
            return {
                items: [
                    {
                        question_number: 1
                    },
                    {
                        question_number: 2
                    }
                ]
            }
        },
        methods: {
            login() {
                if(this.input.email != "" && this.input.pwd != "") {
                    if(this.input.email == "chhun@gmail.com" && this.input.pwd == "123") {
                        // this.$emit("authenticated", true);
                        this.$router.replace({ name: "home" });
                    } else {
                        console.log("The username and / or password is incorrect" + this.input);
                    }
                } else {
                    console.log("A username and password must be present");
                }
            },
            changeQuestion (question_num) {
                console.log(`question ${question_num} is selected`)
            }
        }
    }
</script>

<style scoped>
    #login-form {
        width: 500px;
        border: 1px solid #CCCCCC;
        background-color: #FFFFFF;
        margin: auto;
        margin-top: 200px;
        padding: 20px;
    }
</style>