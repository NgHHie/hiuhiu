<template>
    <div v-if="isShow" class="modal is-active">
        <div class="modal-background" @click="$emit('close')"></div>
        <div class="modal-content">
            <div class="box">
                <p>Lorem ipsum</p>
            </div>
        </div>
        <button class="modal-close is-large" aria-label="close" @click="$emit('close')"></button>
    </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component
export default class ModalIn extends Vue {
    @Prop({ default: false }) private isShow!: boolean;
}
</script>
