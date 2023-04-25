<script setup lang="ts">
import interact from 'interactjs'
import { ref } from 'vue'

const isWasFirstTouch = ref(false)

function onClickFirstTouch() {
  isWasFirstTouch.value = true
}
setTimeout(() => {
  isWasFirstTouch.value = true
}, 4000)
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

function dragMoveListener(event: any) {
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
    <img
      v-show="isWasFirstTouch === false"
      @click="onClickFirstTouch()"
      style="
        transition: 1s all;
        position: absolute;
        z-index: 100;
        width: 400px;
        object-fit: contain;
        top: 250px;
      "
      src="./assets/test.png"
    />
  </transition>

  <div style="width: 100vh; height: 100vh">
    <img
      id="drag-1"
      data-x="32"
      data-y="31"
      class="draggable sticker one"
      src="./assets/stickers/1.webp"
      alt="sticker"
    />
    <img
      id="drag-2"
      data-x="146"
      data-y="-35"
      class="draggable sticker two"
      src="./assets/stickers/2.webp"
      alt="sticker"
    />
    <img
      id="drag-3"
      data-x="-98"
      data-y="205"
      class="draggable sticker three"
      src="./assets/stickers/3.webp"
      alt="sticker"
    />
    <img
      id="drag-4"
      data-x="54"
      data-y="315"
      class="draggable sticker four"
      src="./assets/stickers/4.webp"
      alt="sticker"
    />
    <img
      id="drag-5"
      data-x="152"
      data-y="533"
      class="draggable sticker five"
      src="./assets/stickers/5.webp"
      alt="sticker"
    />
    <img
      id="drag-6"
      data-x="-57"
      data-y="542"
      class="draggable sticker six"
      src="./assets/stickers/6.webp"
      alt="sticker"
    />
    <img
      id="drag-7"
      data-x="188"
      data-y="217"
      class="draggable sticker seven"
      src="./assets/stickers/7.webp"
      alt="sticker"
    />
    <img
      id="drag-8"
      data-x="-64"
      data-y="-34"
      class="draggable sticker eight"
      src="./assets/stickers/8.webp"
      alt="sticker"
    />
    <button @click="onClickOpenSite" action="https://promo.danissimo-club.ru/" class="about">
      ПОДРОБНЕЕ ОБ АКЦИИ
    </button>
    <img style="width: 400px; object-fit: cover" src="./assets/bg.png" />
    <img
      style="left: 0px; position: absolute; bottom: 0px; width: 400px; object-fit: cover"
      src="./assets/acc.png"
    />
  </div>
</template>

<style scoped>
.sticker {
  touch-action: none;
  user-select: none;
  width: 320px;
}

.about {
  position: absolute;
  font-size: 25px;
  border: 3px solid #592718;
  bottom: 25%;
  font-weight: 700;
  left: 45px;
  color: #592718;
  padding: 9px;
  background: transparent;
  transition: 0.5s;
  margin-top: 10px;
}
.about:hover {
  color: white;
  background: #592718;
}
.one {
  cursor: none;
  position: absolute;
  z-index: 10;
  transform: translate(31.84px, 30.845px);
}
.two {
  cursor: none;
  position: absolute;
  z-index: 4;
  transform: translate(146.265px, -35.82px);
}
.three {
  cursor: none;
  position: absolute;
  z-index: 3;
  transform: translate(-98.505px, 204.97px);
}
.four {
  cursor: none;
  position: absolute;
  z-index: 10;
  transform: translate(53.73px, 315.415px);
}
.five {
  cursor: none;
  position: absolute;
  z-index: 2;
  transform: translate(152.235px, 533.32px);
}
.six {
  cursor: none;
  position: absolute;
  z-index: 2;
  transform: translate(-56.715px, 542.275px);
}
.seven {
  cursor: none;
  position: absolute;
  z-index: 2;
  transform: translate(188.055px, 216.91px);
}
.eight {
  cursor: none;
  position: absolute;
  z-index: 7;
  transform: translate(-63.9908px, -33.8566px);
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
