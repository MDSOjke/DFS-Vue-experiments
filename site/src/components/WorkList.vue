<template>
  <div class="work-list">
    <div class="grid">
      <WorkItem v-for="work in works"
        :key="work.title"
        :work="work"/>
    </div>
  </div>
</template>

<script>
import WorkItem from '@/components/WorkItem.vue'

export default {
  name: 'WorkList',
  data: () => {
    return {
      works: [
        {
          title: 'Dogmade',
          link: 'dogmade.com',
          description: 'Awesome posters for your dog!',
          excerpt: 'Awesome posters for your dog!',
          image: require('../assets/Dogmade.png')
        },
        {
          title: 'Basis Berlin',
          link: 'basisberlin.com',
          description: 'Oscar nominated production studio in Berlin',
          excerpt: 'Oscar nominated production studio in Berlin',
          image: require('../assets/Basis Berlin.png')
        }
      ]
    }
  },
  components: {
    WorkItem
  },
  mounted () {
  }
}
</script>

<style scoped lang="less">
  .grid{
    display: flex;
    padding: 30px 5%;
    justify-content: space-around;
    flex-wrap: wrap;
  }
</style>
