<template>
    <div id="login-form">
    <v-form ref="form" v-model="valid" lazy-validation>

        <v-flex xs8>
        <v-text-field
            v-model="email"
            name="input-10-1"
            label="Enter your email address"
            min="100"
            counter
        ></v-text-field>
        </v-flex>

        <v-flex xs8>
        <v-text-field
            v-model="password"
            :append-icon="e1 ? 'visibility' : 'visibility_off'"
            :append-icon-cb="() => (e1 = !e1)"
            :type="e1 ? 'password' : 'text'"
            name="input-10-1"
            label="Enter your password"
            hint="At least 8 characters"
            min="8"
            counter
        ></v-text-field>
        </v-flex>
        <v-btn @click="submit" color="indigo" >submit</v-btn>
        <v-btn @click="clear">clear</v-btn>
    </v-form>
    </div>
</template>

<script>
    
    export default {
        name: 'Login',
        data() {
            return {
                input: {
                    email: "",
                    pwd: ""
                }
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
            submit () {
                if (this.$refs.form.validate()) {
                        // Native form submission is not yet supported
                        axios.post('/api/submit', {
                        name: this.name,
                        email: this.email,
                        select: this.select,
                        checkbox: this.checkbox
                    })
                }
            },
            clear () {
                console.log("clear is clicked")
                this.$refs.form.reset()
                console.log("clear is finshed")
            }
        }
    }
</script>

<style scoped>
    #login-form {
        width: 500px;
        height: 300px;
        background-color: #ffffff;
        margin: auto;
        box-shadow: 2px 2px 2px 1px rgba(0, 0, 0, 0.2);
        margin-top: 200px;
        padding: 20px;
        box-shadow: #000000;
    }
</style>