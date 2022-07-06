<template>
    <v-row align="center">
        <v-col cols="3">
            <v-btn 
                block
                outlined
                disabled
                >
                {{label}}
            </v-btn>
        </v-col>
        <v-col cols="8">
            <slot name="value"></slot>
        </v-col>
        <v-col cols="1" align="left">
            <slot name="validator"></slot>
        </v-col>
    </v-row>
</template>
<script>
export default {
    name: 'GenuiSlot',
    props: ['label'],

    created() {
    },
    data: () => ({
    }),
};
</script>