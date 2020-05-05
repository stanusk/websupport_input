<template>
    <div id="app">
        <div class="container-component">
            <ws-email v-model="emails"></ws-email>
        </div>
        <p>email addresses string: {{ emails }}</p>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import WsEmail from '@/components/WsEmail.vue';

@Component({
    components: { WsEmail },
})
export default class App extends Vue {
    emails = '';
}
</script>

<style lang="scss">
#app {
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    overflow: hidden;

    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;

    .container-component {
        width: 300px;
    }
}
</style>
