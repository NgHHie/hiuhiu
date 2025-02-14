<template>
    <article class="message" v-show="!isHiding">
        <button @click="isHiding=true">X</button>
        <div>
            {{ title }}
        </div>

        <div>
            {{ message }}
        </div>
    </article>
</template>

<script lang="ts">
import {Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class MessageIn extends Vue {
    @Prop() private title! : string
    @Prop() private message! : string

    private isHiding = false
}
</script>