<template>
    <q-input
        outlined
        square
        :value="value"
        @input="onInput"
        label="Emails (comma separated)"
    />
</template>

<script lang="ts">
import { Component, Emit, Prop, Vue } from 'vue-property-decorator';

@Component
export default class WsEmail extends Vue {
    @Prop()
    value = '';

    @Emit('input')
    onInput(value: string) {
        return value;
    }
}
</script>

<style scoped></style>
