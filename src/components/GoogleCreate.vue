<template>
    <v-container>
        <v-row justify="center">
            <v-col md="6">
                <v-card>
                    <v-card-title class="text-h5 text-center">
                        회원가입
                    </v-card-title>
                    <v-card-text>
                        <v-form>
                            <v-text-field label="성함" v-model="name">
                            </v-text-field>
                            <v-text-field label="국가" v-model="national" />
                            <v-text-field label="휴대폰번호" v-model="telNo" />
                            <v-btn type="button" color="primary" block @click="memberCreate()">등록</v-btn>
                        </v-form>
                    </v-card-text>
                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
import axios from 'axios';

export default {
    props: ['token'],
    data() {
        return {
            name: "",
            national: "",
            telNo: "",
        }
    },
    methods: {
        async memberCreate() {
            const registerData = {
                email: this.email,
                password: this.password,
                telNo: this.telNo,
                token: this.token,
            }
            await axios.post("http://localhost:8080/member/google/create", registerData);
            window.location.href = "/";
        }
    }
}
</script>
