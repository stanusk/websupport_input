<template>
    <ws-custom-input
        label="Insert coupon"
        :dense="dense"
        :required="true"
        :value="value"
        :with-button="true"
        :dark="dark"
        @button-click="addCoupon"
        @input="onInput"
    ></ws-custom-input>
</template>

<script lang="ts">
import { Component, Emit, Prop, Vue } from 'vue-property-decorator';
import WsCustomInput from '@/components/WsCustomInput.vue';

@Component({ components: { WsCustomInput } })
export default class WsCoupon extends Vue {
    @Prop({ default: '' })
    value!: string;

    @Prop({ default: false })
    dense!: boolean;

    @Prop({ default: false })
    dark!: boolean;

    @Emit('input')
    onInput(value: string) {
        return value;
    }

    @Emit('add-coupon')
    addCoupon(value: string) {
        return value;
    }
}
</script>

<style scoped lang="scss"></style>
