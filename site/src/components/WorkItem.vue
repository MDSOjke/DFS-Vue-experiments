<template>
  <article class="grid-item" @mouseover.stop="itemHovered = true" @mouseleave.stop="itemHovered = false">
    <div class="grid-item-inner">
      <div class="tile-wrapper" :class="{hovered: itemHovered}">
          <transition-group tag="div" class="tile-wrapper-inner">
            <h1 key="heading"><span class="first-letter" :class="{minified: itemHovered}" key="first-letter">{{ getFirstLetter(work.title) }}</span><span class="all-letters" :class="{minified: itemHovered}" key="all-letters">{{ cutFirstLetter(work.title) }}</span></h1>
            <div class="meta-cont" key="meta" v-show="itemHovered">
              <p>{{work.excerpt}}</p>
              <a class="website-link" :href="`https://${work.link}`" target="_blank">Visit</a>
            </div>
          </transition-group>
      </div>
      <div class="image-wrapper">
        <img :src="work.image" :alt="work.title"/>
      </div>
    </div>
  </article>
</template>

<script>
export default {
  name: 'WorkItem',
  data: () => {
    return {
      itemHovered: false
    }
  },
  props: {
    work: Object
  },
  methods: {
    getFirstLetter (text) {
      return text.toString().split('')[0]
    },
    cutFirstLetter (text) {
      let textStr = text.toString().split('')
      textStr.shift()
      return textStr.join('')
    }
  },
  mounted () {
  }
}
</script>

<style scoped lang="less">
  .grid-item{
    width: 50%;
    padding: 10px;
    flex-grow: 0;
    flex-shrink: 0;
    @media (min-width: 769px) {
      box-sizing: border-box;
    }
    @media(max-width: 768px){
      width: 100%;
      flex-basis: 100%;
      padding: 40px 20px;
    }
  }
  .grid-item-inner{
    position: relative;
    height: 100%;
    width: 200px;
    margin: 0 auto;
  }
  h1{
    font-weight: 600;
    font-size: 1.25em;
    height: 100%;
    span {
      &.first-letter{
        font-size: 4em;
        font-family: 'Rubik', Arial, Helvetica, sans-serif;
        transition: 0.3s all;
        transform: translateY(-50px);
        transform-origin: 50% 50%;
        &.minified{
          transition: 0.3s all;
          font-size: 3em;
          color: #413c58;
          transform: translateY(0);
          transform-origin: 50% 50%;
          text-shadow: none;
        }
      }
      &.all-letters{
        transition: all 1s 0.3s;
        filter: blur(0px);
        opacity: 1;
        margin-left: -0.25em;
        &.minified{
          transition: all 0.1s;
          letter-spacing: -0.5em;
          filter: blur(12px);
          opacity: 0;
        }
      }
    }
  }
  .tile-wrapper{
    position: relative;
    z-index: 1;
    height: 200px;
    display: flex;
    justify-content: center;
    align-items: center;
    transition: background 0.5s;
    .tile-wrapper-inner{
      display: flex;
      height: 100%;
      justify-content: right;
      width: 100%;
      align-items: center;
      >h1, >div.meta-cont{
        flex-grow: 0;
        flex-shrink: 0;
      }
      >div.meta-cont{
        flex-grow: 1;
        max-width: 150px;
        margin-left: 20px;
        padding: 10px 20px;
        background: linear-gradient(to right, rgba(255,255,255,0) 0%, white 40%);
        a{
          text-decoration: none;
          background-color: #413c58;
          padding: 0.5em;
          display: inline-block;
          margin-top: 0.5em;
          color: white;
        }
      }
    }
    &.hovered{
      .tile-wrapper-inner{
        justify-content: left;
      }
    }
  }
  .image-wrapper{
    width: 200px;
    height: 200px;
    border-radius: 50%;
    position: absolute;
    top: 0;
    left: 0;
    overflow: hidden;
    img{
      object-fit: cover;
      width: 100%;
      min-height: 100%;
      opacity: 0.4;
    }
  }
  .v-enter, .v-leave-to {
      opacity: 0;
  }
  .v-move{
      transition: all 0.1s, opacity 0.5s;
  }
  .v-enter-active.v-move {
    transition: all 0.1s, opacity 0.3s;
  }
  .v-leave-active {
    position: absolute;
    transition: all 0.5s, opacity 0.5s;
  }
</style>
