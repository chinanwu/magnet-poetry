<template>
  <button class="Magnet" draggable="true" v-draggable>
    {{ word }}
  </button>
</template>

<script>
export default {
  name: "Magnet",
  props: {
    word: String,
  },
  directives: {
    draggable: {
      mounted(el) {
        let currentX,
          currentY,
          initialX,
          initialY,
          xOffset = 0,
          yOffset = 0,
          active = false;

        const handleMouseMove = (e) => {
          if (active) {
            e.preventDefault();

            currentX = e.clientX - initialX;
            currentY = e.clientY - initialY;

            xOffset = currentX;
            yOffset = currentY;

            el.style.transform =
              "translate3d(" + currentX + "px, " + currentY + "px, 0)";
          }
        };

        const handleMouseUp = () => {
          initialX = currentX;
          initialY = currentY;
          active = false;
          document
            .getElementById("app")
            .removeEventListener("mousemove", handleMouseMove);
          document
            .getElementById("app")
            .removeEventListener("mouseup", handleMouseUp);
        };

        el.addEventListener("mousedown", (e) => {
          e.preventDefault();
          initialX = e.clientX - xOffset;
          initialY = e.clientY - yOffset;
          active = true;
          document
            .getElementById("app")
            .addEventListener("mousemove", handleMouseMove);
          document
            .getElementById("app")
            .addEventListener("mouseup", handleMouseUp);
        });
      },
    },
  },
};
</script>

<style lang="less" scoped>
.Magnet {
  padding: 1rem;
  cursor: grab;
  user-select: none;
  font-size: 2rem;
  background: white;
  text-align: center;
  border: 1px solid #efefef;
}
</style>

<!-- https://www.kirupa.com/html5/drag.htm -->
