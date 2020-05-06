<template>
    <div id="app">
        <div class="container-row">
            <input-testing-container title="Email: single | required">
                <ws-email v-model="emailSingle"></ws-email>
            </input-testing-container>

            <input-testing-container title="Email: single | optional">
                <ws-email v-model="emailSingle" :required="false"></ws-email>
            </input-testing-container>

            <input-testing-container title="Email: dark" :dark="true">
                <ws-email
                    v-model="emailSingle"
                    :dark="true"
                    :required="false"
                ></ws-email>
            </input-testing-container>

            <input-testing-container title="Email: multiple | required">
                <ws-email v-model="emailMultiple" mode="multiple"></ws-email>
            </input-testing-container>

            <input-testing-container title="Email: dense">
                <ws-email v-model="emailSingle" :dense="true"></ws-email>
            </input-testing-container>
        </div>

        <div class="container-row">
            <input-testing-container
                title="Coupon"
                icon="local_activity"
                color="blue"
            >
                <ws-coupon v-model="coupon" @add-coupon="addCoupon"></ws-coupon>
            </input-testing-container>

            <input-testing-container
                title="Coupon: dense"
                icon="local_activity"
                color="blue"
            >
                <ws-coupon
                    v-model="coupon"
                    :dense="true"
                    @add-coupon="addCoupon"
                ></ws-coupon>
            </input-testing-container>
        </div>
    </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import WsEmail from '@/components/WsEmail.vue';
import InputTestingContainer from '@/components/InputTestingContainer.vue';
import WsCoupon from '@/components/WsCoupon.vue';

@Component({
    components: { InputTestingContainer, WsEmail, WsCoupon },
})
export default class App extends Vue {
    emailSingle = '';
    emailMultiple = '';
    coupon = '';

    addCoupon(coupon: string) {
        console.log(coupon);
    }
}
</script>

<style lang="scss">
@import 'src/styles/ws.variables';

#app {
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    overflow: hidden;

    display: flex;
    justify-content: space-around;
    align-items: center;
    flex-wrap: wrap;

    .container-row {
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        align-items: center;
    }

    .text-ws-dark {
        color: $ws-emerald;
    }

    .bg-ws-dark {
        background: $ws-emerald;
    }
}
</style>
