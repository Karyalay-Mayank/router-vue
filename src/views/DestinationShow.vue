<template>
    <section v-if="destination" class="destination">
        <h1>
            {{ destination.name }}
        </h1>
        <div class="destination-details">
            <img :src="`/images/${destination.image}`" :alt="destination.name" />
            <p>
                {{ destination.description }}
            </p>
        </div>
    </section>
</template>

<script>
import sourceData from '@/data.json'

export default {
    data () {
        return {
            destination: null
        }
    },
    computed: {
        destinationId () {
            return parseInt(this.$route.params.id);
        },

        // destination () {
        //     return sourceData.destinations.find(destination => destination.id === this.destinationId)
        // }
    },

    async created () {
        this.InitData();

        // or
        // this.$watch(
        //     () => this.$route.params, this.InitData
        // ) // Can be also done using :key="$route.path"
    },

    methods: {
        // Instead we can use watchers in created
        async InitData () {
            const response = await fetch(`https://travel-dummy-api.netlify.app/${this.$route.params.slug}.json`);
            this.destination = await response.json();
        }
    }
}
</script>