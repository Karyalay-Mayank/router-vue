<template>
    <div id="nav">
        <router-link id="logo" to="/">Abhyas Router</router-link>
        <router-link v-for="destination in destinations" :key="destination.id"
            :to="{ name: 'destination.show', params: { id: destination.id, slug: destination.slug } }">{{
                destination.name
            }}</router-link>
    </div>
</template>

<script>
import sourceData from '@/data.json'

export default {
    data () {
        return {
            destinations: sourceData.destinations
        }
    }
}
</script>

<style lang="css">
#nav .router-abhyas-active-class {
    padding: 2px 3px;
    color: #2c3e50;
    background-color: #fff;
    border-radius: 2px;
}
</style>