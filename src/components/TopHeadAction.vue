<template>
    <div>
        <button
            class="top-head-action"
            @click="switchComponent('ChatField')"
            :disabled="currentComp === 'ChatField'">
            <i class="material-icons" >textsms</i>
        </button>
        <button
            class="top-head-action"
            @click="switchComponent('ChatFieldMicrophone')"
            :disabled="currentComp === 'ChatFieldMicrophone'">
            <i class="material-icons" >mic</i>
        </button>

    </div>
</template>

<style lang="sass" scoped>
@import '@/style/mixins'

.top-head-action
    @include reset
    display: flex
    margin: 8px 0
    padding: 10px 12px
    border-radius: 40px 0 0 40px
    border: var(--border)
    border-right: none
    cursor: pointer
    color: var(--text-primary)
    transition: padding .25s var(--animation-timing)

    &:hover
        padding-right: 20px
</style>

<script>
import { bus } from '../main.js';

export default {
    name: 'TopHeadAction',
    props: {
        title: {
            type: String,
            default: ''
        },
        icon: {
            type: String,
            default: ''
        },
        currentComp: {
            type: String,
            required: true
        }  
    },

    methods: {
        switchComponent(comp) {
            bus.$emit('switchComp', comp);
        }
    }
}
</script>
