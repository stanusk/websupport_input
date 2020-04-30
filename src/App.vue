<template>
    <div id="app">
        <q-input v-model="text" label="Standard" />
    </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component({
    components: {},
})
export default class App extends Vue {
    text = '';
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
}
</style>
