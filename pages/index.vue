<template>
  <!-- <Tutorial/> -->
  <h2>Welcome to the best corny dad jokes app on the web</h2>
  
</template>

<script>
export default {
  // name: 'IndexPage', // 컴포넌트가 아니라서 다른 곳에서 import 할 이유가 없기 때문에 굳이 작성할 필요 없음
  head() { // => 최초 initial 설정은 nuxt.config.js 에서 작성  
    return {
      title: 'Welcome to Dad Jokes', 
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Best place for corny dad jokes'
        }
      ]
    }
  }
}
</script>
