<template>
    <Head>
        <title></title>
        <meta type="description" content="Layout infomation" head-key="description">
    </head>
    <section class="p-6 bg-gray-200">
        <header class="flex justify-between">
            <div class="flex items-center">
                <h1 class="font-bold text-lg">My App</h1>

                <p class="text-sm ml-4">Welcome {{ this.$page.props.auth.user.username }}</p>
            </div>
            <Nav />
        </header>
    </section>

    <section class="p-6">
        <div class="max-w-2xl mx-auto bg-gray">
            <slot />
        </div>
    </section>
</template>

<script setup>
import Nav from "./Nav.vue";
import { Head } from "@inertiajs/inertia-vue3";
</script>
