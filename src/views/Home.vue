<template>
  <div class="topnavAndBanner">
    <Topnav/>
    <div class="banner">
      <h1>Tiger UI</h1>
      <h2>一个简单易用的UI框架</h2>
      <p class="actions">
        <a href="">Github</a>
        <router-link to="/doc/intro">开始</router-link>
      </p>
    </div>
  </div>
  <div class="features">
    <ul>
      <li>
        <svg>
          <use xlink:href="#icon-Vue"></use>
        </svg>
        <h3>基于 Vue 3</h3>
        <p>骄傲地使用了 Vue 3 Composition API</p>
      </li>
      <li>
        <svg>
          <use xlink:href="#icon-ts"></use>
        </svg>
        <h3>基于 TypeScript </h3>
        <p>源代码采用 TypeScript 书写（非严格检查）</p>
      </li>
      <li>
        <svg>
          <use xlink:href="#icon-lights"></use>
        </svg>
        <h3>代码易读</h3>
        <p>每个组件的源代码都极其简洁</p>
      </li>
    </ul>
  </div>

</template>

<script lang='ts'>
import Topnav from '../components/Topnav.vue';

export default {
  components: {Topnav}
};
</script>

<style lang='scss' scoped>
$green: #00a7aa;
$color: #f4f4f4;
.topnavAndBanner {
  background: linear-gradient(135deg, rgba(2,0,36,1) 0%, rgba(167,211,253,1) 0%, rgba(186,190,248,1) 100%);
  clip-path: ellipse(80% 60% at 50% 40%);
}
.banner {
  color: $color;
  padding: 100px 0;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;

  > .actions {
    padding: 8px 0;

    a {
      background: #f792b5;
      color: white;
      margin: 0 8px;
      display: inline-block;
      padding: 8px 24px;
      border-radius: 20px;
      text-decoration: none;

      &:hover {
        background: #efabc4 ;
      }
    }
  }
}
.features {
  margin: 64px auto;
  padding: 0 16px;
  @media(min-width: 800px) {
    width: 800px;
    > ul{
      >li{
        width: 50%;
      }
    }
  }
  @media(min-width: 1200px) {
    width: 1200px;
    > ul{
      >li{
        width:33.333%
      }
    }
  }

  > ul {
    display: flex;
    flex-wrap: wrap;

    > li {
      margin: 16px 0;
      display: grid;
      justify-content: start;
      align-content: space-between;
      grid-template-areas:
        "icon title"
        "icon text";
      grid-template-columns: 80px auto;
      grid-template-rows: 1fr auto;

      > svg {
        grid-area: icon;
        width: 64px;
        height: 64px;
      }

      > h3 {
        grid-area: title;
        font-size: 28px;
      }

      > p {
        grid-area: text
      }
    }


  }
}

</style>
