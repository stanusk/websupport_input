<template>
    <div class="container-component" :class="{ dark }">
        <q-chip :dark="dark" square outline size="md" class="q-my-sm q-mx-none">
            <q-avatar :icon="icon" :text-color="color" />
            {{ title }}
        </q-chip>
        <slot></slot>
    </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator';
import WsEmail from '@/components/WsEmail.vue';

@Component({
    components: { WsEmail },
})
export default class InputTestingContainer extends Vue {
    @Prop({ default: 'email' })
    icon!: string;

    @Prop({ default: 'red' })
    color!: string;

    @Prop()
    title!: string;

    @Prop({ default: false })
    dark!: boolean;
}
</script>

<style lang="scss">
@import 'src/styles/ws.variables';

.container-component {
    width: 300px;
    padding: 5px;

    &.dark {
        background-color: $ws-char-coal;
    }
}
</style>
