<template>
    <Head title="User" />

    <app-layout>
        <template #header>
            User List
        </template>

        <add-new-button :href="route('users.create')" />

        <data-table :collections="users" :filters="filters" :dateFilter="true">
            <template #head>
                <th class="py-3 px-2 text-left">ID</th>
                <th class="py-3 px-2 text-left">Name</th>
                <th class="py-3 px-2 text-left">Email</th>
                <th class="py-3 px-2 text-left">Phone</th>
                <th class="py-3 px-2 text-left">Type</th>
                <th class="py-3 px-2 text-center">Action</th>
            </template>
            <template #default="{ item: user }">
                <td class="py-3 px-2 text-left">{{ user.id }}</td>
                <td class="py-3 px-2 text-left">{{ user.name }}</td>
                <td class="py-3 px-2 text-left">{{ user.email }}</td>
                <td class="py-3 px-2 text-left">{{ user.phone }}</td>
                <td class="py-3 px-2 text-left">{{ user.typeName }}</td>
                <td class="py-2.5 px-2">
                    <div class="flex justify-center items-center gap-1 md:gap-2">
                        <action-button-show :href="route('users.show', user.id)" />
                        <action-button-edit :href="route('users.edit', user.id)" />
                    </div>
                </td>
            </template>
        </data-table>
    </app-layout>
</template>

<script>
import AppLayout from "@/Layouts/App.vue";
import { Head, Link } from "@inertiajs/inertia-vue3";
import DataTable from "@/Components/DataTable.vue";
import ActionButtonShow from "@/Components/ActionButtonShow.vue";
import ActionButtonEdit from "@/Components/ActionButtonEdit.vue";
import AddNewButton from '@/Components/AddNewButton.vue';

export default {
    components: {
        AppLayout,
        DataTable,
        Head,
        Link,
        ActionButtonShow,
        ActionButtonEdit,
        AddNewButton,
    },
    props: {
        users: { type: Object, default: {} },
        filters: { type: Object, default: {} },
    },
};
</script>
