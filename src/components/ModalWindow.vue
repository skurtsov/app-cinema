<template>
  <div class="play" @click="ModalShow = true">
    <i class="fa-solid fa-circle-play"></i>
  </div>
  <div class="modal-backdrop" v-if="ModalShow">
    <div class="modal-overlay" @click="ModalShow = false"></div>
    <div class="modal">
      <header class="modal-header">
        <button type="button" class="btn-close" @click="ModalShow = false">
          x
        </button>
      </header>

      <section class="modal-body">
        <slot name="body"
          ><iframe
            width="100%"
            height="98%"
            :src="UrlTitle"
            title="YouTube video player"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
            allowfullscreen
          ></iframe
        ></slot>
      </section>
    </div>
  </div>
</template>

<script>
export default {
  name: "ModalWindow",
  props: ["UrlTitle"],
  data() {
    return {
      ModalShow: false,
    };
  },
};
</script>
<style>
.modal-backdrop {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.3);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal {
  background: #1a1a1a;
  box-shadow: 2px 2px 20px 1px;
  overflow-x: auto;
  display: flex;
  flex-direction: column;
  z-index: 1;
  width: 1000px;
  height: 700px;
}

.modal-header,
.modal-footer {
  padding: 15px;
  display: flex;
}

.modal-header {
  position: relative;
  color: #4aae9b;
  justify-content: space-between;
}

.modal-footer {
  border-top: 1px solid #eeeeee;
  flex-direction: column;
  justify-content: flex-end;
}

.modal-body {
  position: relative;
  padding: 20px 10px;
  height: 100%;
}

.btn-close {
  position: absolute;
  top: 0;
  right: 0;
  border: none;
  font-size: 20px;
  padding: 10px;
  cursor: pointer;
  font-weight: bold;
  color: #4aae9b;
  background: transparent;
}

.btn-green {
  color: white;
  background: #4aae9b;
  border: 1px solid #4aae9b;
  border-radius: 2px;
}
.play {
  font-size: 50px;
  height: 100px;
  color: #fff;
  position: absolute;
  left: 49%;
  top: 32%;
}
.modal-overlay {
  position: absolute;
  z-index: 0;
  width: 100%;
  height: 100%;
  background-color: #0000004d;
}
</style>
