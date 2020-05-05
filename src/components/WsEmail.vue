<template>
    <ws-custom-input
        :value="value"
        @input="onInput"
        :required="required"
        :autogrow="mode !== 'single'"
        :label="label"
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
