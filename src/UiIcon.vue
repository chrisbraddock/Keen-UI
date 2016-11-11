<template>
    <i
        class="ui-icon material-icons" :class="[icon]" v-text="removeText ? null : icon"
        aria-hidden="true"
        @click="onClick"
    ></i>
</template>

<script>
export default {
    name: 'ui-icon',

    props: {
        icon: {
            type: String,
            required: true
        },
        removeText: {
            type: Boolean,
            default: false
        }
    },

    methods: {
        onClick() {
            this.$emit('click')
        }
    }
};
</script>

<style lang="stylus">
@import './styles/imports';

.ui-icon {
    font-size: 24px;
    width: 1em;
    height: 1em;
    display: inline-block;
    cursor: inherit;
    vertical-align: middle;
}
</style>
