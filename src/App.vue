<script setup lang="ts">
import interact from 'interactjs'
import { ref } from 'vue'

const isWasFirstTouch = ref(false)

function onClickFirstTouch() {
  isWasFirstTouch.value = true
}
function onClickOpenSite() {
  window.open('https://promo.danissimo-club.ru/')
}

interact('.draggable').draggable({
  inertia: true,
  modifiers: [
    interact.modifiers.restrictRect({
      endOnly: true
    })
  ],
  autoScroll: true,

  listeners: {
    move: dragMoveListener
  }
})

function dragMoveListener(event) {
  var target = event.target

  var x = (parseFloat(target.getAttribute('data-x')) || target.style.translate) + event.dx
  var y = (parseFloat(target.getAttribute('data-y')) || target.style.translate) + event.dy
  target.style.transform = 'translate(' + x + 'px, ' + y + 'px)'

  target.setAttribute('data-x', x)
  target.setAttribute('data-y', y)
}
</script>

<template>
  <transition name="fade">
    <div
      style="transition: 1s all; position: absolute; z-index: 100"
      v-show="isWasFirstTouch === false"
      @click="onClickFirstTouch()"
    >
      <img src="./assets/first.png" />
    </div>
  </transition>

  <img
    id="drag-1"
    data-x="30"
    data-y="-35"
    class="draggable sticker one"
    src="./assets/stickers/1.png"
    alt="sticker"
  />
  <img
    id="drag-2"
    data-x="269"
    data-y="-743"
    class="draggable sticker two"
    src="./assets/stickers/2.png"
    alt="sticker"
  />
  <img
    id="drag-3"
    data-x="-131"
    data-y="-848"
    class="draggable sticker three"
    src="./assets/stickers/3.png"
    alt="sticker"
  />
  <img
    id="drag-4"
    data-x="102"
    data-y="-1244"
    class="draggable sticker four"
    src="./assets/stickers/4.png"
    alt="sticker"
  />
  <img
    id="drag-5"
    data-x="291"
    data-y="-1692"
    class="draggable sticker five"
    src="./assets/stickers/5.png"
    alt="sticker"
  />
  <img
    id="drag-6"
    data-x="-160"
    data-y="-2195"
    class="draggable sticker six"
    src="./assets/stickers/6.png"
    alt="sticker"
  />
  <img
    id="drag-7"
    data-x="337"
    data-y="-3291"
    class="draggable sticker seven"
    src="./assets/stickers/7.png"
    alt="sticker"
  />
  <img
    id="drag-8"
    data-x="-128"
    data-y="-4240"
    class="draggable sticker eight"
    src="./assets/stickers/8.png"
    alt="sticker"
  />
  <div style="position: absolute; top: 0; z-index: 1">
    <button @click="onClickOpenSite" action="https://promo.danissimo-club.ru/" class="about">
      ПОДРОБНЕЕ ОБ АКЦИИ
    </button>
    <img src="./assets/bg.png" />
  </div>
</template>

<style scoped>
.sticker {
  touch-action: none;
  user-select: none;
}

.about {
  position: absolute;
  font-size: 30px;
  border: 5px solid #592718;
  bottom: 15%;
  font-weight: 700;
  left: 200px;
  color: #592718;
  padding: 24px;
  background: transparent;
  transition: 0.5s;
}
.about:hover {
  color: white;
  background: #592718;
}
.one {
  cursor: none;
  position: relative;
  z-index: 10;
  transform: translate(30.3939px, -35.0834px);
}
.two {
  cursor: none;
  position: relative;
  transform: translate(269px, -743px);
  z-index: 4;
}
.three {
  cursor: none;
  position: relative;
  transform: translate(-131.333px, -848.667px);
  z-index: 3;
}
.four {
  cursor: none;
  position: relative;
  transform: translate(102.75px, -1244px);
  z-index: 10;
}
.five {
  cursor: none;
  position: relative;
  z-index: 2;
  transform: translate(291px, -1692px);
}
.six {
  cursor: none;
  position: relative;
  transform: translate(-160.667px, -2195.33px);
  z-index: 2;
}
.seven {
  cursor: none;
  position: relative;
  transform: translate(337.333px, -3291.67px);
  z-index: 2;
}
.eight {
  cursor: none;
  position: relative;
  transform: translate(-128px, -4240px);
  z-index: 7;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
