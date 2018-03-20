<template>
    <div class="col-xs-12 col-sm-6">
        <p v-if="serverId != ''">Server #{{ serverId }} Status: {{ serverStatus }} <button @click="resetServer">Reset</button></p>
        <p v-else>Select server</p>
    </div>
</template>

<script>
    import { eventBus } from './main';

    export default {
        data: function() {
            return{
                serverId: '',
                serverStatus: ''
            }
        },
        created() {
            eventBus.$on('showDetails', (server) => {
                this.serverId = server.serverId;
                this.serverStatus = server.serverStatus;
            });
        },
        methods: {
        resetServer() {
            this.serverStatus = 'Normal';
            eventBus.$emit('resetServer', {serverId: this.serverId, serverStatus: this.serverStatus});
        }
    }
    }
</script>

<style>

</style>
