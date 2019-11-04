<template>
  <div class="home">
    <VariantsRoller />
    <HeadingOnBackground />
    <WorkList />
  </div>
</template>
<style lang="less">
</style>

<script>
// @ is an alias to /src
import VariantsRoller from '@/components/VariantsRoller.vue'
import HeadingOnBackground from '@/components/HeadingOnBackground.vue'
import WorkList from '@/components/WorkList.vue'

export default {
  name: 'home',
  components: {
    VariantsRoller,
    HeadingOnBackground,
    WorkList
  }
}
</script>
