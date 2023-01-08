<template>
    <Head>
        <title>Users</title>
        <meta type="description" content="Users infomation" head-key="description">
    </Head>
    <div class="flex justify-between">
        <h1 class="text-3xl">Users</h1>

        <input v-model="search" type="text" placeholder="Search....." class="border px-2 rounded-lg">

    </div>

    <table class="mt-6 border-separate border border-slate-400 ...">
        <tbody>
        <tr v-for="user in users.data" :key="user.id">
            <td class="border border-slate-300 ...">{{ user.name }}</td>
        </tr>
        </tbody>
    </table>

    <!-- Paginator -->
    <Pagination :links="users.links"/>


</template>

<script setup>
    import { Head} from '@inertiajs/inertia-vue3';
    import Pagination from "../Shared/Pagination.vue";
    import {ref, watch} from "vue";
    import {Inertia} from "@inertiajs/inertia";

    let props = defineProps({
        users: Object,
        filters: Object
    });
    let search = ref(props.filters.search);
    watch(search, value => {
       Inertia.get('/users', {search: value}, {
           preserveState: true,
           replace: true
       })
    });
</script>

<script>
    import Layout from "../Shared/Layout.vue";
    export default {
        layout: Layout
    }
</script>


<style scoped>

</style>
