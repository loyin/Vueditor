<style>
  .ve-code textarea {
    /*safari*/
    position: absolute;
    box-sizing: border-box;
    display: block;
    width: 100%;
    height: 100%;
    outline: none;
    border: none;
    resize: none;
    font-size: 14px;
  }
</style>
<template>
  <div class="ve-code" v-show="currentView == 'sourceCode'">
    <textarea ref="codemirror">{{content}}</textarea>
  </div>
</template>

<script>

  export default {
    data () {
      return {
        editor: null
      }
    },
    computed: {
      currentView: function () {
        return this.$store.state.currentView;
      },
      content: function () {
        return this.$store.state.content;
      }
    },
    watch: {
      'currentView': function (val) {
        if(val == 'design'){
          this.updateContent(this.$refs.codemirror.value);
        }
      }
    },
    methods: {
      updateContent (content) {
        this.$store.dispatch('updateContent', content);
      }
    }
  }
</script>