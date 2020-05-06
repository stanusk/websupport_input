<template>
    <div class="container" :class="{ dark }">
        <q-input
            class="input"
            :class="{ 'with-button': this.withButton }"
            :autogrow="autogrow"
            :dense="dense"
            :label="label"
            :rules="appendedRules"
            :value="value"
            :dark="dark"
            :color="dark ? 'ws-dark' : ''"
            @input="onInput"
            outlined
            square
            no-error-icon
        >
            <template v-if="!required" v-slot:append>
                <i class="append-text">(Optional)</i>
            </template>
        </q-input>
        <q-btn
            v-if="withButton"
            class="button"
            flat
            @click="onButtonClick(value)"
        >
            <template v-slot:default>
                <q-icon class="icon" :class="{ dense }" name="add" />
            </template>
        </q-btn>
    </div>
</template>

<script lang="ts">
import { Component, Emit, Prop, Vue } from 'vue-property-decorator';

@Component
export default class WsCustomInput extends Vue {
    @Prop({ default: '' })
    value!: string;

    @Prop({ default: '' })
    label!: string;

    @Prop({ default: false })
    autogrow!: boolean;

    @Prop({ default: false })
    required!: boolean;

    @Prop({ default: () => [] })
    rules!: ((value: any) => true | string)[];

    @Prop({ default: false })
    withButton!: boolean;

    @Prop({ default: false })
    dense!: boolean;

    @Prop({ default: false })
    dark!: boolean;

    get appendedRules() {
        // todo: localization
        const ruleRequired = (val: string) => !!val || 'Field is required';
        // todo: make adding rules more user-friendly
        // todo: document adding rules
        return [...(this.required ? [ruleRequired] : []), ...this.rules];
    }

    @Emit('input')
    onInput(value: string) {
        return value;
    }

    @Emit('button-click')
    onButtonClick(value: string) {
        return value;
    }
}
</script>

<style scoped lang="scss">
@import 'src/styles/ws.variables';

.container {
    display: flex;

    .input {
        flex-grow: 1;

        ::v-deep .q-field__control {
            &:before {
                border: 2px solid $ws-lighter;
            }
        }

        .append-text {
            font-size: 0.8rem;
        }

        &.with-button {
            ::v-deep .q-field__control:before,
            ::v-deep .q-field__control:after,
            ::v-deep .q-field__control:hover:after,
            ::v-deep .q-field__control:hover:before {
                border-right: none;
            }
        }
    }

    &.dark {
        .input {
            ::v-deep .q-field__control {
                &:before {
                    border: 2px solid $ws-davys-gray;
                }

                background-color: $ws-medium-jungle-gray;

                &:focus-within {
                    background-color: $ws-char-coal;
                }
            }
        }
    }

    .button {
        background-color: $ws-davys-gray;
        color: white;
        border-radius: 0;

        margin-bottom: 20px;

        .icon {
            font-size: 56px;
            &.dense {
                font-size: 40px;
            }
        }

        ::v-deep .q-btn__wrapper {
            padding: 0;
        }
    }
}
</style>
