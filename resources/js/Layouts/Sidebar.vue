<script setup>
    import MainNav from '@/Components/MainNav.vue'
    import ApplicationLogo from '@/Components/ApplicationLogo.vue';
    import Dropdown from '@/Components/Dropdown.vue';
    import DropdownLink from '@/Components/DropdownLink.vue';
    import NavLink from '@/Components/NavLink.vue';
    import ResponsiveNavLink from '@/Components/ResponsiveNavLink.vue';
    import { ref } from 'vue';
    import { Link } from '@inertiajs/vue3';

    const showingNavigationDropdown = ref(false);

    let width = ref('w-[250px]')
    let hidden = ref("")
    let isCollapsed = ref(false)

    function toggleWidth() {
        if(width.value == 'w-[250px]') {
            width.value = 'w-[100px]'
            hidden.value = "hidden"
            isCollapsed.value =!isCollapsed.value

        }else {
            width.value = ['w-[250px]']
            hidden.value = ""
            isCollapsed.value =!isCollapsed.value

        }
    }
</script>

<template>

<div class="flex min-h-screen">
    <div id="sidebar" class="bg-gray-400 p-6 duration-500" :class="width" style="position: relative;">
        <button class="text-xl text-tahiti" @click="toggleWidth" style="position: absolute; right: 10px; top:10px">
            <i class="fa-solid fa-bars"></i>
        </button>
        <div id="branding" :class="hidden">
            <img src="data:image/png;base64,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" alt="Logo"
                class="w-[170px] h-[170px] mx-auto rounded-full object-cover">
            <h1 class="text-3xl text-bold text-center text-gray-800 my-6">CODE BREAKERS</h1>

        </div>
        <MainNav :collapse="isCollapsed"/>

    </div>

    <div id="container" class="flex-1 ">
        <nav class="bg-white border-b border-gray-100">
                <!-- Primary Navigation Menu -->
                <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                    <div class="flex justify-between h-16">
                        <div class="flex">
                            <!-- Logo -->
                            <div class="shrink-0 flex items-center">
                                <Link :href="route('dashboard')">
                                    <ApplicationLogo
                                        class="block h-9 w-auto fill-current text-gray-800"
                                    />
                                </Link>
                            </div>

                            <!-- Navigation Links -->
                            <!-- <div class="hidden space-x-8 sm:-my-px sm:ml-10 sm:flex">
                                <NavLink :href="route('dashboard')" :active="route().current('dashboard')">
                                    Dashboard
                                </NavLink>
                            </div> -->
                        </div>

                        <div class="hidden sm:flex sm:items-center sm:ml-6">
                            <!-- Settings Dropdown -->
                            <div class="ml-3 relative">
                                <Dropdown align="right" width="48">
                                    <template #trigger>
                                        <span class="inline-flex rounded-md">
                                            <button
                                                type="button"
                                                class="inline-flex items-center px-3 py-2 border border-transparent text-sm leading-4 font-medium rounded-md text-gray-500 bg-white hover:text-gray-700 focus:outline-none transition ease-in-out duration-150"
                                            >
                                                {{ $page.props.auth.user.name }}

                                                <svg
                                                    class="ml-2 -mr-0.5 h-4 w-4"
                                                    xmlns="http://www.w3.org/2000/svg"
                                                    viewBox="0 0 20 20"
                                                    fill="currentColor"
                                                >
                                                    <path
                                                        fill-rule="evenodd"
                                                        d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z"
                                                        clip-rule="evenodd"
                                                    />
                                                </svg>
                                            </button>
                                        </span>
                                    </template>

                                    <template #content>
                                        <DropdownLink :href="route('profile.edit')"> Profile </DropdownLink>
                                        <DropdownLink :href="route('logout')" method="post" as="button">
                                            Log Out
                                        </DropdownLink>
                                    </template>
                                </Dropdown>
                            </div>
                        </div>

                        <!-- Hamburger -->
                        <div class="-mr-2 flex items-center sm:hidden">
                            <button
                                @click="showingNavigationDropdown = !showingNavigationDropdown"
                                class="inline-flex items-center justify-center p-2 rounded-md text-gray-400 hover:text-gray-500 hover:bg-gray-100 focus:outline-none focus:bg-gray-100 focus:text-gray-500 transition duration-150 ease-in-out"
                            >
                                <svg class="h-6 w-6" stroke="currentColor" fill="none" viewBox="0 0 24 24">
                                    <path
                                        :class="{
                                            hidden: showingNavigationDropdown,
                                            'inline-flex': !showingNavigationDropdown,
                                        }"
                                        stroke-linecap="round"
                                        stroke-linejoin="round"
                                        stroke-width="2"
                                        d="M4 6h16M4 12h16M4 18h16"
                                    />
                                    <path
                                        :class="{
                                            hidden: !showingNavigationDropdown,
                                            'inline-flex': showingNavigationDropdown,
                                        }"
                                        stroke-linecap="round"
                                        stroke-linejoin="round"
                                        stroke-width="2"
                                        d="M6 18L18 6M6 6l12 12"
                                    />
                                </svg>
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Responsive Navigation Menu -->
                <div
                    :class="{ block: showingNavigationDropdown, hidden: !showingNavigationDropdown }"
                    class="sm:hidden"
                >
                    <div class="pt-2 pb-3 space-y-1">
                        <ResponsiveNavLink :href="route('dashboard')" :active="route().current('dashboard')">
                            Dashboard
                        </ResponsiveNavLink>
                    </div>

                    <!-- Responsive Settings Options -->
                    <div class="pt-4 pb-1 border-t border-gray-200">
                        <div class="px-4">
                            <div class="font-medium text-base text-gray-800">
                                {{ $page.props.auth.user.name }}
                            </div>
                            <div class="font-medium text-sm text-gray-500">{{ $page.props.auth.user.email }}</div>
                        </div>

                        <div class="mt-3 space-y-1">
                            <ResponsiveNavLink :href="route('profile.edit')"> Profile </ResponsiveNavLink>
                            <ResponsiveNavLink :href="route('logout')" method="post" as="button">
                                Log Out
                            </ResponsiveNavLink>
                        </div>
                    </div>
                </div>
            </nav>
        <header class="bg-white shadow" v-if="$slots.header">
            <div class="max-w-7xl mx-auto py-6 px-4 sm:px-6 lg:px-8">
                <slot name="header" />
            </div>
        </header>

            <!-- Page Content -->
        <main>
            <slot />
        </main>
    </div>
</div>

</template>
