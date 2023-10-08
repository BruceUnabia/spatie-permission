<script setup>
import Sidebar from '@/Layouts/Sidebar.vue';
import ClientCard from '@/Components/ClientCard.vue'
import Pagination from '@/Components/Pagination.vue'
import PrimaryButton from '@/Components/PrimaryButton.vue'
import { Head , Link} from '@inertiajs/vue3';

const props = defineProps({
    clients: Object
})
</script>

<template>
     <Head title="Client" />

    <div>
        <Sidebar>
            <template #header>
                <h2 class="font-semibold text-center text-xl text-gray-800 leading-tight">Client List</h2>
            </template>

            <div class="py-12">

                <div class="max-w-7xl mx-auto sm:px-6 lg:px-8 flex flex-wrap">


                    <ClientCard v-for=" client in props.clients.data" :client="client" :key="client.id"/>
                </div>
                <Pagination :links="clients.links" class="mt-6 text-center"/>
            </div>

        </Sidebar>


    </div>
</template>
