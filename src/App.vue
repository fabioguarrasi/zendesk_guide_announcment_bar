<template>
  <div class="announcments-bar" 
    :style="{'background-color': backgroundColor, 'color': textColor }">
    <button 
      class="close"
      @click="closeBar()">
      <img src="./assets/close.svg" alt="">
    </button>
    <div class="icon">
      <img src="./assets/megaphone.svg" alt="">
    </div>
    <div class="content">
      <ul>
        <li v-for="item in items" v-cloak>
          <h3>{{item.title}}</h3>
          <p>{{item.description}}</p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'zd-announcments',
    delimiters: ['{[{', '}]}'],
    props: {
      // items: {
      //   type: Array,
      //   required: false,
      // },
      icon: {
        type: String,
        required: false,
        default: 'megaphone.svg'
      },
      backgroundColor: {
        type: String,
        required: false,
        default: '#0072EF'
      },
      textColor: {
        type: String,
        required: false,
        default: '#FFFFFF'
      }
    },
    data: function() {
      return {
        items: [{title: 'Title announcment', description: 'description'}]
      }
    },
    methods: {
      closeBar: function() {
        this.$destroy();
      }
    }
  }
</script>

<style lang="scss">
[v-cloak] {
  display: none;
}

.announcments-bar {
  display: flex;
  align-items: center;
  justify-content: space-between;

  .close {
    flex-grow: 0;
    background-color: transparent;
    border: none;
    outline: none;
    display: flex;
    order: 1;

    img {
      width: 15px;
      align-self: flex-start;
    }
  }

  .icon {
    display: flex;
    flex-grow: 0;
    align-self: stretch;
    background-color: rgba(0,0,0,.2);
    padding: 10px;

    img {
      width: 50px;
      align-self: center;
    }
  }

  .content {
    flex-grow: 1;
    padding: 15px;
    justify-content: flex-start;

    ul {
      display: flex;
      flex-direction: column;
      list-style-type: none;
      margin: 0;
      padding: 0;
      
      li {
        margin-bottom: 5px;

        &:last-child {
          margin-bottom: 0;
        }
      }
    }

    h3,
    p {
      margin: 0 0 2px;
      line-height: 1.3;
    }
  }
}
</style>
