<script setup>
import Card from "../components/Card.vue";
import paginationLinks from "../components/paginationLinks.vue";
import InputField from "../components/InputField.vue";
import { router, useForm } from "@inertiajs/vue3";

const params = route().params;
const props = defineProps({
    listings: Object,
    searchTerm: String,
});
const username = params.user_id
    ? props.listings.data.find((i) => i.user_id === Number(params.user_id)).user
          .name
    : null;
const form = useForm({
    search: props.searchTerm,
});
const search = () => {
    router.get(route("home"), {
        search: form.search,
        user_id: params.user_id,
        tag: params.tag,
    });
};
</script>

<template>
    <Head title="-Latest Listings" />
    <!-- remove filter -->

    <!-- search filter -->
    <div class="flex items-center justify-between mb-4">
        <div class="flex items-center gap-2">
            <Link
                class="px-2 py-1 rounded-md bg-indigo-500 text-white flex items-center gap-2"
                v-if="params.tag"
                :href="route('home', { ...params, tag: null, page: null })"
            >
                {{ params.tag }}
                <i class="fa-solid fa-xmark"></i>
            </Link>
            <Link
                class="px-2 py-1 rounded-md bg-indigo-500 text-white flex items-center gap-2"
                v-if="params.search"
                :href="route('home', { ...params, search: null, page: null })"
            >
                {{ params.search }}
                <i class="fa-solid fa-xmark"></i>
            </Link>

            <Link
                class="px-2 py-1 rounded-md bg-indigo-500 text-white flex items-center gap-2"
                v-if="params.user_id"
                :href="route('home', { ...params, user_id: null, page: null })"
            >
                {{ username }}
                <i class="fa-solid fa-xmark"></i>
            </Link>
        </div>
        <div class="w-1/4">
            <form @submit.prevent="search">
                <InputField
                    type="search"
                    label=""
                    icon="magnifying-glass"
                    placeholder="Search..."
                    v-model="form.search"
                />
            </form>
        </div>
    </div>
    <div v-if="Object.keys(listings.data).length">
        <div class="grid grid-cols-3 gap-4">
            <div v-for="listing in listings.data" :key="listing.id">
                <Card :listing="listing" />
            </div>
        </div>
        <div class="mt-8">
            <paginationLinks :paginator="listings" />
        </div>
    </div>
    <div v-else>there are no listing</div>
</template>
