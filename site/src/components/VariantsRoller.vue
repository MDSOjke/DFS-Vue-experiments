<template>
  <div class="variants-roller">
      <transition-group tag="h1" name="variants-roller">
        <span class="static-text" :key="weDoText">{{weDoText}}</span><span class="task-text" :key="taskSelected">{{taskSelected}}</span><span class="static-text" :key="forText">{{forText}}</span><span class="platform-text" :key="platformSelected">{{platformSelected}}</span>
      </transition-group>
  </div>
</template>

<script>
export default {
  name: 'VariantsRoller',
  data: () => {
    return {
      tasks: [
        'rigorous PSD-to-HTML',
        'abyss-deep templating',
        'strict pixel-perfect',
        'powerful server-side scripts',
        'almighty server-less API',
        'tough API integrations',
        'lovely UI integrations',
        'boring code-refactoring',
        'overwhelming styling',
        'sneaky AWS configurations'
      ],
      platforms: [
        'Squarespace',
        'Shopify',
        'Vue',
        'static websites',
        'SPA'
      ],
      taskSelected: 'rigorous PSD-to-HTML',
      platformSelected: 'Squarespace',
      weDoText: 'We do ',
      forText: ' for '
    }
  },
  mounted () {
    const self = this
    setInterval(() => {
      self.taskSelected = self.tasks[Math.floor(Math.random() * self.tasks.length)]
      self.platformSelected = self.platforms[Math.floor(Math.random() * self.platforms.length)]
    }, 4000)
  }
}
</script>

<style scoped lang="less">

.variants-roller{
  vertical-align: middle;
  height: 98vh;
  transition: all 0.5s;
  display: flex;
  justify-content: center;
  align-items: center;
  span{
    transition: all 1s;
    margin: 0 3px;
    display: inline-block;
    background-color: white;
    backface-visibility: hidden;
    font-size: 2em;
    line-height: 2;
  }
  .variants-roller-enter-active, .variants-roller-leave-active{
      transition: all 1s;
      transform: rotateX(0deg);
      backface-visibility: none;
  }
  .variants-roller-enter, .variants-roller-leave-to {
      opacity: 0;
  }
  .variants-roller-enter {
      transform-origin: top;
      transform: rotateX(-180deg);
  }
  .variants-roller-leave-to {
      transform-origin: bottom;
      transform: rotateX(180deg);
  }
  .variants-roller-leave-active {
    position: absolute;
  }
  .variants-roller-move{
      transition: all 0.5s;
  }

  .task-text, .platform-text{
    font-weight: 600;
  }
}

</style>
