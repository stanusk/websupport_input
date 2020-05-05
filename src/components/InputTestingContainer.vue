<template>
    <div class="container-component">
        <q-chip square outline size="md" class="q-my-sm q-mx-none">
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
}
</script>

<style lang="scss"></style>
