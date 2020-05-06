<template>
    <ws-custom-input
        :required="true"
        :value="value"
        :with-button="true"
        @button-click="addCoupon"
        @input="onInput"
        label="Insert coupon"
    ></ws-custom-input>
</template>

<script lang="ts">
import { Component, Emit, Prop, Vue } from 'vue-property-decorator';
import WsCustomInput from '@/components/WsCustomInput.vue';

@Component({ components: { WsCustomInput } })
export default class WsCoupon extends Vue {
    @Prop({ default: '' })
    value!: string;

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
