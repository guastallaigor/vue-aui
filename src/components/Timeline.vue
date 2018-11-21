<template>
  <section class="timeline">
    <ul v-if="items">
      <li v-for="(item, key) in items" :key="key">
        <div class="layout nowrap-column">
          <p class="title-header layout">{{ item.title }}</p>
          <span v-if="item.content">{{ item.content }}</span>
        </div>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  props: {
    items: Array
  }
}
</script>

<style>
.layout {
  display: flex;
}

.nowrap-column {
  flex-flow: column nowrap;
}

.spacer {
  flex-flow: 1;
}

.timeline .title-header {
  border-bottom: 1px solid #fff;
  font-size: 1.2em;
  margin-bottom: .1em;
  width: 100%;
  margin-left: -15px;
  padding: 0 15px .1em 15px;
  background: #0052cc;
  color: #fff;
}

.timeline {
  margin-top: 50px;
  margin-bottom: 50px;
}

.timeline ul li {
  list-style-type: none;
  position: relative;
  width: 2px;
  margin: 0 auto;
  padding-top: 15px;
  background: rgba(0,0,0,0.12);
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
  width: 400px;
  padding: 0 15px 5px 15px;
  margin-top: -30px;
  border: 1px solid #0052cc;
  background: #fff;
  border-radius: 3px;
}

.timeline ul li div::before {
  content: '';
  position: absolute;
  top: 3px;
  left: 100%;
  width: 0;
  height: 0;
  border-style: solid;
}

.timeline ul li:nth-child(odd) div {
  left: 38px;
}

.timeline ul li:nth-child(odd) div::before {
  left: -13px;
  border-width: 8px 13px 8px 0;
  border-color: transparent #0052cc transparent transparent;
}

.timeline ul li:nth-child(even) div {
  left: -460px;
}

.timeline ul li:nth-child(even) div::before {
  right: -13px;
  border-width: 8px 0 8px 13px;
  border-color: transparent transparent transparent #0052cc;
}

@media screen and (max-width: 900px) and (min-width: 0px) {
  .timeline ul li div {
    width: 220px;
  }

  .timeline ul li:nth-child(even) div {
    left: 38px;
  }

  .timeline ul li:nth-child(even) div::before {
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
