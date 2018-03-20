<template>
    <div class="col-xs-12 col-sm-6">
        <ul class="list-group">
            <app-server-status v-for="server in servers" :key="server.id" :server-id="server.id" :server-status="server.status"></app-server-status>
        </ul>
    </div>
</template>

<script>
import ServerStatus from './ServerStatus'
import { eventBus } from './main';

export default {
    data: function() {
        return {
            servers: [
                { id: 1, status: 'Normal' },
                { id: 2, status: 'Critical' },
                { id: 3, status: 'Unknown' },
                { id: 4, status: 'Normal' }
            ]
        };
    },
    components: {
        'app-server-status' : ServerStatus
    },
    created() {
        eventBus.$on('resetServer', (server) => {
            console.log(server);
            this.servers[server.serverId-1].status = server.serverStatus;
        });
    }
}
</script>

<style>

</style>
