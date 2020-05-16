<template>
    <ws-custom-input
        :autogrow="mode !== 'single'"
        :label="label"
        :required="required"
        v-bind="$attrs"
        v-on="$listeners"
    ></ws-custom-input>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';
import WsCustomInput from '@/components/WsCustomInput.vue';

@Component({ components: { WsCustomInput } })
export default class WsEmail extends Vue {
    @Prop({ default: 'single' })
    mode!: 'single' | 'multiple';

    @Prop({ default: true })
    required!: boolean;

    get label() {
        const single = 'Email';
        const multiple = 'Emails (comma separated)';
        return this.mode === 'single' ? single : multiple;
    }
}
</script>

<style scoped lang="scss"></style>
