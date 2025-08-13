<template>
    구글 로그인 중....
</template>

<script>
import axios from 'axios';

export default {
    created() {
        const code = new URL(window.location.href).searchParams.get("code");
        this.sendCodeToServer(code);
    },
    methods: {
        async sendCodeToServer(code) {
            const response = await axios.post("http://localhost:8080/member/google/doLogin", { code });
            const token = response.data.token;
            localStorage.setItem("token", token);
            window.location.href = "/";
        },
        async checkMember() {
            const member = {
                email: this.email,
                socialType: "GOOGLE",
            }
            await axios.post("http://localhost:8080/member/findmember", member);
        }
    }
}
</script>