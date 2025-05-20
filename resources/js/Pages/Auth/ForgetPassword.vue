<script setup>
import Container from "../../components/Container.vue";
import InputField from "../../components/InputField.vue";
import PrimaryBtn from "../../components/PrimaryBtn.vue";
import { useForm } from "@inertiajs/vue3";
import ErrorMessages from "../../components/ErrorMessages.vue";
import SessionMessages from "../../components/SessionMessages.vue";

const form = useForm({
    email: "",
});

const submit = () => {
    form.post(route("password.email"));
};
defineProps({ status: String });
</script>

<template>
    <Head title="-Forget Password" />
    <Container class="w-1/2">
        <div class="mb-8 text-center">
            <p>
                Forgot your password? No problem. Just let us know your email
                address and we will email you a password reset link that will
                allow you to choose a new one.
            </p>
        </div>
        <!-- error -->
        <ErrorMessages :errors="form.errors" />
        <SessionMessages :status="status" />
        <form class="space-y-6" @submit.prevent="submit">
            <InputField label="Email" icon="at" v-model="form.email" />

            <PrimaryBtn :disabled="form.processing">
                Send Password Reset Link
            </PrimaryBtn>
        </form>
    </Container>
</template>
