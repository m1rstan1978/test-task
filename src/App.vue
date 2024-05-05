<template>
  <div class="square">
    <div class="square__container">
      <div class="square__verticall">
        <div
          class="square__item"
          v-for="item in mathRandomVerticall"
          :key="item"
        >
          <div
            class="square__item_block"
            :style="{
              borderRadius: Math.round(Math.random() * 50) + 'px',
            }"
            @mouseenter="setAnimation($event.target)"
            @mouseleave="delAnimation($event.target)"
          >
            {{ Math.round(Math.random() * 100) }}
          </div>
          <div
            class="square__item_block horizontall"
            v-for="el in mathRandomHorizontal"
            :key="el"
            :style="{
              borderRadius: Math.round(Math.random() * 50) + 'px',
            }"
            ref="square_horizontal"
            @mouseenter="setAnimation($event.target)"
            @mouseleave="delAnimation($event.target)"
          >
            {{ Math.round(Math.random() * 100) }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      mathRandomVerticall: Math.round(Math.random() * 100) + 100,
      mathRandomHorizontal: Math.round(Math.random() * 10) + 10,
    };
  },
  methods: {
    setAnimation(target) {
      const borderRadius = parseFloat(target.style.borderTopLeftRadius);
      const result = borderRadius + borderRadius * 0.2;
      target.style.borderRadius = result + "px";
    },
    delAnimation(target) {
      const borderRadius = parseFloat(target.style.borderTopLeftRadius);
      const result = borderRadius - borderRadius * 0.2;
      target.style.borderRadius = result + "px";
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
.square {
  padding: 100px;
}
.square__verticall {
  display: flex;
  align-items: flex-start;
  flex-direction: column;
}
.square__item {
  margin-bottom: 20px;
  display: flex;
  align-items: flex-start;
}

.square__item_block {
  border: 2px solid red;
  width: 50px;
  height: 50px;
  border-radius: 10px;
  font-size: 22px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
}
.square__item_content {
  display: flex;
  align-items: flex-start;
}
.horizontall {
  margin-left: 20px;
}
</style>
