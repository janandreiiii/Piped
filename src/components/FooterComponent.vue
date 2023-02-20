<template>
    <footer class="text-center py-4 rounded-xl children:(mx-3) w-full mt-10">
        <a aria-label="GitHub" href="https://github.com/TeamPiped/Piped" target="_blank">
            <font-awesome-icon :icon="['fab', 'github']" />
            <span class="ml-2" v-t="'actions.source_code'" />
        </a>
        <a href="https://docs.piped.video/" target="_blank">
            <font-awesome-icon :icon="['fa', 'book']" />
            <span class="ml-2" v-t="'actions.documentation'" />
        </a>
        <a href="https://github.com/TeamPiped/Piped#donations" target="_blank">
            <font-awesome-icon :icon="['fab', 'bitcoin']" />
            <span class="ml-2" v-t="'actions.donations'" />
        </a>
        <a v-if="statusPageHref" :href="statusPageHref">
            <font-awesome-icon :icon="['fa', 'server']" />
            <span class="ml-2" v-t="'actions.status_page'" />
        </a>
        <a v-if="donationHref" :href="donationHref">
            <font-awesome-icon :icon="['fa', 'donate']" />
            <span class="ml-2" v-t="'actions.instance_donations'" />
        </a>
    </footer>
</template>

<script>
export default {
    data() {
        return {
            donationHref: null,
            statusPageHref: null,
        };
    },
    props: {
        config: {
            type: Object,
        },
    },
    watch: {
        config: {
            handler() {
                this.donationHref = this.config?.donationUrl;
                this.statusPageHref = this.config?.statusPageUrl;
            },
        },
    },
};
</script>

<style>
footer {
    @apply bg-light-900;
}
.dark footer {
    @apply bg-dark-800;
}
</style>
