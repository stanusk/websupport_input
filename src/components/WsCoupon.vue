<template>
    <ws-custom-input
        :value="value"
        @input="onInput"
        label="Insert coupon"
        :required="true"
        :with-button="true"
    >
        <q-btn size="lg" class="button" flat @click="addCoupon(value)">
            <template v-slot:default>
                <q-icon class="icon" name="add" />
            </template>
        </q-btn>
    </ws-custom-input>
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

<style scoped lang="scss">
.button {
    background-color: black;
    color: white;
    border-radius: 0;

    /* todo: make adaptive */
    margin-bottom: 20px;

    .icon {
        /* todo: make adaptive */
        font-size: 56px;
    }

    ::v-deep .q-btn__wrapper {
        padding: 0;
    }
}
</style>
