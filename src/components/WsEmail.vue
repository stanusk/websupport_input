<template>
    <q-input
        :value="value"
        :rules="appendedRules"
        @input="onInput"
        label="Emails (comma separated)"
        outlined
        square
        autogrow
        no-error-icon
    >
        <template v-if="!required" v-slot:append>
            <i class="append-text">(Optional)</i>
        </template>
    </q-input>
</template>

<script lang="ts">
import { Component, Emit, Prop, Vue } from 'vue-property-decorator';

@Component
export default class WsEmail extends Vue {
    @Prop()
    value = '';

    @Prop({ default: false })
    required!: boolean;

    @Prop({ default: () => [] })
    rules!: ((value: any) => true | string)[];

    get appendedRules() {
        // todo: localization
        const ruleRequired = (val: string) => !!val || 'Field is required';
        // todo: make adding rules more user-friendly
        // todo: document adding rules
        return [...(this.required ? [ruleRequired] : []), ...this.rules];
    }

    @Emit('input')
    onInput(value: string) {
        return value;
    }
}
</script>

<style scoped lang="scss">
.append-text {
    font-size: 0.8rem;
}
</style>
