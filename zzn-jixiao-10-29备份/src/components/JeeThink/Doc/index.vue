<template>
  <div>
    <svg-icon icon-class="link" @click="goto"/>
  </div>
</template>

<script>
export default {
  name: 'JeeThinkDoc',
  data() {
    return {
      url: 'https://item.taobao.com/item.htm?id=629682899366'
    }
  },
  methods: {
    goto() {
      window.open(this.url)
    }
  }
}
</script>