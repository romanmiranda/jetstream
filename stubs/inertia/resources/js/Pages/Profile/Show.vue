<script setup>
import AppLayout from '@/Layouts/AppLayout.vue';
import DeleteUserForm from '@/Pages/Profile/Partials/DeleteUserForm.vue';
import LogoutOtherBrowserSessionsForm from '@/Pages/Profile/Partials/LogoutOtherBrowserSessionsForm.vue';
import SectionBorder from '@/Components/SectionBorder.vue';
import TwoFactorAuthenticationForm from '@/Pages/Profile/Partials/TwoFactorAuthenticationForm.vue';
import UpdatePasswordForm from '@/Pages/Profile/Partials/UpdatePasswordForm.vue';
import UpdateProfileInformationForm from '@/Pages/Profile/Partials/UpdateProfileInformationForm.vue';

defineProps({
    confirmsTwoFactorAuthentication: Boolean,
    sessions: Array,
});
</script>

<template>
    <AppLayout title="Profile">
        <template #header>
            <h2 class="h4 font-weight-bold">
                Profile
            </h2>
        </template>


        <div v-if="$page.props.jetstream.canUpdateProfileInformation" class="mb-5">
            <UpdateProfileInformationForm :user="$page.props.auth.user" />

            <SectionBorder />
        </div>

        <div v-if="$page.props.jetstream.canUpdatePassword" class="mb-5">
            <UpdatePasswordForm class="mt-10" />

            <SectionBorder />
        </div>

        <div v-if="$page.props.jetstream.canManageTwoFactorAuthentication" class="mb-5">
            <TwoFactorAuthenticationForm
                :requires-confirmation="confirmsTwoFactorAuthentication"
                class="mt-10"
            />

            <SectionBorder />
        </div>

        <LogoutOtherBrowserSessionsForm :sessions="sessions" class="mb-5" />

        <template v-if="$page.props.jetstream.hasAccountDeletionFeatures">
            <SectionBorder />

            <DeleteUserForm class="mb-5" />
        </template>


    </AppLayout>
</template>
