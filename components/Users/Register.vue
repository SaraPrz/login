<template>
    <v-form
        ref="entryForm"
        v-model="valid"
        lazy-validation
    >
        <v-text-field
            v-model="firstName"
            :counter="15"
            label="First Name"
            required
            :rules="fNameRules"
            maxlength="15" 
        ></v-text-field>
        <v-text-field
            v-model="lastName"
            :counter="20"
            label="Last Name"
            required
            :rules="lNameRules"
            maxlength="20" 
        ></v-text-field>
        <v-text-field
            v-model="phoneNumber"
            :counter="13"
            label="Phone Number"
            required
            :rules="phoneRules"
            maxlength="13" 
        ></v-text-field>
        <v-text-field
            v-model="email"
            label="E-mail"
            required
            :rules="emailRules"
        ></v-text-field>
        <v-text-field
            v-model="password"
            label="Password"
            type="password"
            :rules="passwordRules"
            required
        ></v-text-field>
        <v-text-field 
            v-model="confirmPass"
            label="Confirm Password"
            type="password"
            :rules="pwdConfirm"
            required
        ></v-text-field>
        <v-checkbox
            v-model="checkbox"
            value="1"
            label="Agree PrivacyPolicy"
            type="checkbox"
            required
        ></v-checkbox>

        <v-btn
            :disabled="!valid"
            class="mr-4"
            type="submit"
            color="success"
            @click="validate"
        >
            submit
        </v-btn>
        <v-btn @click="clear">
            clear
        </v-btn>
    </v-form>
</template>

<script>
export default {
    name: 'Register',
    Data()  {
        return {
            valid: true ,
            firstName : "",
            lastName : "",
            phoneNumber: "",
            email: "",
            password : "",
            confirmPass: "",
            fNameRules : [
                v => !!v || 'first name is required',
                v => (v && v.length <= 15 && v.length >= 4) || 'Name must be more than 4 and less than 10 characters',
            ],
            lNameRules : [
                v => !!v || 'last name is required',
                v => (v && v.length <= 20 && v.length >= 4) || 'Name must be more than 4 and less than 10 characters',
            ],
            phoneRules : [
                v => !!v || 'phone number is required',
                v => /^(\+98|0098|98|0)?9\d{9}$/.test(v) || 'phone number must start with 09 , 9 , +989 '
            ],
            emailRules: [
                v => !!v || 'email is required',
                v => /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/.test(v) || 'E-mail must be valid'
            ],
            
            passwordRules: [
                v => !!v || "Required.",
                v => {
                const pattern = /^(?=.*[a-z])(?=.*[A-Z])(?=.*[0-9])(?=.{8,})/;
                return (
                    pattern.test(v) ||
                    "Min. 8 characters with at least one capital letter, a number ."
                );
            }
            ],
        
        pwdConfirm:[ 
            v => !!v || 'Confirm password', 
            v => v === this.password || 'Passwords do not match'
            ],
        }
    },
    methods: {
        validate() {
            this.$refs.entryForm.validate()
        },
        clear() {
            this.$refs.entryForm.reset()
        }
    }
}
</script>