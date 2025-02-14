<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <li v-for="(name,index) in names" :key="index" v-text="name"></li>
    <input type="text" ref="input" name="" id="" v-model="strTmp">
    <button id="btn" v-bind:title="tit" @click="addName" :class="{'is-loading':isLoading}">add name</button>
    <h2 v-text="strTmp"></h2>
    <MessageIn title="Hello World" message="Hiep dep trai"></MessageIn>
    <button @click="showModal = true">Open Modal</button>
    <ModalIn :isShow="showModal" @close="showModal = false"></ModalIn>
    <!-- <button @click=""></button> -->
  </div>
</template>

<script lang="ts">
import { Component, Model, Prop, Vue } from 'vue-property-decorator';
import MessageIn from './MessageIn.vue';
import ModalIn from './ModalIn.vue';


@Component({
  components: {
    MessageIn,
    ModalIn
  }
})
export default class HelloWorld extends Vue {
  @Prop() private msg!: string;

  private names : string[] = ['hiep', 'hang']
  private strTmp = 'hiep'
  private tit = "click to add name"
  private isLoading = false;
  private showModal = false; 
  private addName() : void {
    const input = this.$refs.input as HTMLInputElement
    const newName = input.value
    if(newName.trim()) {
      this.names.push(newName)
      input.value = ''
      input.focus()
      this.isLoading = true
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.is-loading {
  background-color: #42b983;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
