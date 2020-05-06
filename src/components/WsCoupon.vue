<template>
    <div class="container">
        <q-input
            :value="value"
            @input="onInput"
            label="Insert coupon"
            class="input"
            outlined
            square
            no-error-icon
        >
        </q-input>
        <q-btn size="lg" class="button" flat @click="addCoupon(value)">
            <template v-slot:default>
                <!-- todo: solve without size -->
                <q-icon name="add" size="56px" />
            </template>
        </q-btn>
    </div>
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
.container {
    display: flex;
    .input {
        flex-grow: 1;
    }
    /* todo: fix colors */
    .button {
        background-color: black;
        color: white;
        border-radius: 0;

        ::v-deep .q-btn__wrapper {
            padding: 0;
        }
    }
}
</style>
