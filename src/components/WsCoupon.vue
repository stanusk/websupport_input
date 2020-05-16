<template>
    <ws-custom-input
        label="Insert coupon"
        :with-button="true"
        @button-click="addCoupon"
        v-on="$listeners"
        v-bind="$attrs"
    ></ws-custom-input>
</template>

<script lang="ts">
import { Component, Emit, Vue } from 'vue-property-decorator';
import WsCustomInput from '@/components/WsCustomInput.vue';

@Component({ components: { WsCustomInput } })
export default class WsCoupon extends Vue {
    @Emit('add-coupon')
    addCoupon(value: string) {
        return value;
    }
}
</script>

<style scoped lang="scss"></style>
