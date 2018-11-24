<template>
  <section class="timeline">
    <ul v-if="items && items.length">
      <li v-for="(item, key) in items" :key="key" @click="$emit('click', item)">
        <div class="layout nowrap-column" :style="alignContentAndBorderColor">
          <span class="arrow" :style="borderStyle(key)"></span>
          <span class="title-header layout" :style="alignTitleAndBackgroundColor">{{ item.title }} - {{ key }}</span>
          <span v-if="item.content">{{ item.content }}</span>
        </div>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  props: {
    items: Array,
    alignContent: {
      type: String,
      default: 'left'
    },
    alignTitle: {
      type: String,
      default: 'flex-start'
    },
    color: {
      type: String,
      default: '#0052cc'
    }
  },
  computed: {
    alignTitleAndBackgroundColor() {
      return `justify-content:${this.alignTitle};background:${this.color}`
    },
    alignContentAndBorderColor() {
      return `text-align:${this.alignContent};border:1px solid ${this.color};`
    }
  },
  methods: {
    borderStyle(key) {
      return parseInt(key, 10) % 2 === 0 ?
        `border-color: transparent ${this.color} transparent transparent;` :
        `border-color: transparent transparent transparent ${this.color};`
    }
  }
}
</script>

<style scoped>
.timeline .layout {
  display: flex;
}

.timeline .nowrap-column {
  flex-flow: column nowrap;
}

.timeline .title-header {
  border-bottom: 1px solid #fff;
  font-size: 1.2em;
  width: 100%;
  margin-left: -15px;
  padding: 0 15px 0 15px;
  color: #fff;
  background: #0052cc;
}

.timeline {
  margin-top: 50px;
  margin-bottom: 50px;
}

.timeline ul li {
  list-style-type: none;
  position: relative;
  margin: 0 auto;
  padding-top: 15px;
  width: 2px;
  background: #c3c3c3;
}

.timeline ul li::after {
  content: '';
  position: absolute;
  left: 50%;
  top: -14px;
  transform: translateX(-50%);
  width: 20px;
  height: 20px;
  border-radius: 50%;
  background: #fff;
  border: 1px solid #ef5350;
}

.timeline ul li::before {
  content: '';
  position: absolute;
  left: 50%;
  top: -9.5px;
  z-index: 2;
  align-self: center;
  transform: translateX(-50%);
  width: 13px;
  height: 13px;
  border-radius: 50%;
  background: #ef5350;
}

.timeline ul li div {
  position: relative;
  padding: 0 15px 5px 15px;
  margin-top: -30px;
  border: 1px solid #0052cc;
  border-radius: 3px;
  cursor: pointer;
  background: #fff;
  will-change: box-shadow;
  transition: .3s box-shadow;
  min-width: 320px;
}

.timeline ul li div:hover {
  box-shadow: 0px 3px 1px -2px rgba(0,0,0,0.2), 0px 2px 2px 0px rgba(0,0,0,0.14), 0px 1px 5px 0px rgba(0,0,0,0.12);
}

.timeline ul li .arrow {
  content: '';
  position: absolute;
  top: 3px;
  height: 0;
  width: 0;
  padding: 0;
  margin: 0;
  left: 100%;
  width: 0;
  height: 0;
  border-style: solid;
}

.timeline ul li:nth-child(odd) div {
  left: 38px;
}

.timeline ul li:nth-child(odd) .arrow {
  left: -13px;
  border-width: 8px 13px 8px 0;
  border-color: transparent #0052cc transparent transparent;
}

.timeline ul li:nth-child(even) div {
  left: -388px;
}

.timeline ul li:nth-child(even) .arrow {
  right: -13px;
  border-width: 8px 0 8px 13px;
  border-color: transparent transparent transparent #0052cc;
}

@media screen and (max-width: 900px) and (min-width: 0px) {
  .timeline ul li div {
    min-width: 220px;
  }

  .timeline ul li:nth-child(even) div {
    left: 38px;
  }

  .timeline ul li:nth-child(even) .arrow {
    left: -13px;
    border-width: 8px 13px 8px 0;
    border-color: transparent #0052cc transparent transparent;
  }

  .timeline ul li {
    margin: 0;
    margin-left: -35px;
  }

  .timeline ul li {
    padding-bottom: 25px;
  }
}
</style>
