<script setup>
import Container from "../../../components/Container.vue";
import Title from "../../../components/Title.vue";
import InputField from "../../../components/InputField.vue";
import { useForm } from "@inertiajs/vue3";
import PrimaryBtn from "../../../components/PrimaryBtn.vue";
import ErrorMessages from "../../../components/ErrorMessages.vue";
import { ref } from "vue";

const showConfirmPassword = ref(false);

const form = useForm({
    password: "",
});

const submit = () => {
    form.delete(route("profile.destroy"), {
        onFinish: () => form.reset(),
        preserveScroll: true,
    });
};
</script>

<template>
    <Container class="mb-6">
        <div class="mb-6">
            <Title>Delete Account</Title>
            <p>
                Once your account is deleted, all of its resources data will be
                permanently deleted. This action cannot be undone.
            </p>
        </div>

        <ErrorMessages :errors="form.errors" />

        <div v-if="showConfirmPassword">
            <form @submit.prevent="submit" class="flex items-end gap-4">
                <InputField
                    label="Confirm Password"
                    icon="key"
                    type="password"
                    class="w-1/2"
                    v-model="form.password"
                />

                <PrimaryBtn :disabled="form.processing">Confirm</PrimaryBtn>

                <button
                    @click="showConfirmPassword = false"
                    class="text-indigo-500 font-medium underline dark:text-indigo-400"
                >
                    Cancel
                </button>
            </form>
        </div>

        <button
            v-if="!showConfirmPassword"
            @click="showConfirmPassword = true"
            class="px-6 py-2 rounded-lg bg-red-500 text-white"
        >
            <i class="fa-solid fa-triangle-exclamation mr-2"></i>
            Delete Account
        </button>
    </Container>
</template>
