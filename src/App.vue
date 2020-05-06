<template>
    <div id="app">
        <input-testing-container title="Email: single | required">
            <ws-email v-model="emailSingle"></ws-email>
        </input-testing-container>

        <input-testing-container title="Email: single | optional">
            <ws-email v-model="emailSingle" :required="false"></ws-email>
        </input-testing-container>

        <input-testing-container title="Email: multiple | required">
            <ws-email v-model="emailMultiple" mode="multiple"></ws-email>
        </input-testing-container>

        <input-testing-container
            title="Coupon"
            icon="local_activity"
            color="blue"
        >
            <ws-coupon v-model="coupon" @add-coupon="addCoupon"></ws-coupon>
        </input-testing-container>
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
#app {
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    overflow: hidden;

    display: flex;
    flex-direction: column;
    justify-content: space-around;
    align-items: center;

    .container-component {
        width: 300px;
    }
}
</style>
