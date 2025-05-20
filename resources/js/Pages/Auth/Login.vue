<script setup>
import Container from "../../components/Container.vue";
import Title from "../../components/Title.vue";
import TextLink from "../../components/TextLink.vue";
import InputField from "../../components/InputField.vue";
import PrimaryBtn from "../../components/PrimaryBtn.vue";
import { useForm } from "@inertiajs/vue3";
import ErrorMessages from "../../components/ErrorMessages.vue";
import SessionMessages from "../../components/SessionMessages.vue";
import CheckBox from "../../components/CheckBox.vue";

const form = useForm({
    email: "",
    password: "",
    remember: null,
});

defineProps({
    status: String,
});
const submit = () => {
    form.post(route("login"), {
        onFinish: () => form.reset("password"),
    });
};
</script>

<template>
    <Head title="-Login" />
    <Container class="w-1/2">
        <div class="mb-8 text-center">
            <Title>Login To Your Account</Title>
            <p>
                Need an account ?
                <TextLink routeName="register" label="Register" />
            </p>
        </div>
        <!-- error -->
        <ErrorMessages :errors="form.errors" />
        <SessionMessages :status="status" />
        <form class="space-y-6" @submit.prevent="submit">
            <InputField label="Email" icon="at" v-model="form.email" />

            <InputField
                label="Password"
                type="password"
                icon="key"
                v-model="form.password"
            />
            <div class="flex items-center justify-between">
                <CheckBox name="remember" v-model="form.remember"
                    >Remeber Me</CheckBox
                >
                <TextLink
                    routeName="password.request"
                    label="Forget Password?"
                />
            </div>

            <PrimaryBtn :disabled="form.processing"> Login </PrimaryBtn>
        </form>
    </Container>
</template>
