<template>
    <ws-custom-input
        :autogrow="mode !== 'single'"
        :dense="dense"
        :label="label"
        :required="required"
        :value="value"
        @input="onInput"
    ></ws-custom-input>
</template>

<script lang="ts">
import { Component, Emit, Prop, Vue } from 'vue-property-decorator';
import WsCustomInput from '@/components/WsCustomInput.vue';

@Component({ components: { WsCustomInput } })
export default class WsEmail extends Vue {
    @Prop({ default: 'single' })
    mode!: 'single' | 'multiple';

    @Prop({ default: '' })
    value!: string;

    @Prop({ default: true })
    required!: boolean;

    @Prop({ default: false })
    dense!: boolean;

    @Emit('input')
    onInput(value: string) {
        return value;
    }

    get label() {
        const single = 'Email';
        const multiple = 'Emails (comma separated)';
        return this.mode === 'single' ? single : multiple;
    }
}
</script>

<style scoped lang="scss"></style>
