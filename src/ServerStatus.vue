<template>
    <li class="list-group-item" @click="loadDetails">
        Server #{{ serverId }} Status: {{ serverStatus }}
    </li>
</template>

<script>
import { eventBus } from './main';

export default {
    props: ['serverId', 'serverStatus'],
    methods: {
        loadDetails() {
            eventBus.$emit('showDetails', {serverId: this.serverId, serverStatus: this.serverStatus});
        }
    }
}
</script>

<style>

</style>
