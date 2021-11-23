<template>
  <div class="home">
      <div class="home__inner">
        <button class="Button"
        @click="decreaseCount"
        >-</button>
      <input class="inputCount"
        type="number" 
        :value="count"
        :min="minCount"
        :max="maxCount"
      />
      <button class="Button"
        @click="increaseCount"
        >+</button>
      </div>
  </div>
</template>

<script>
    export default {
      name: 'MyOneComponents',
      data() {
        return {
          count: 0,
          maxCount: 20,
          minCount: 0

        }
      },
      methods: {
        increaseCount() {
          if (this.count < this.maxCount) {
            this.count++
            console.log(this.$root._uid);
          }
        },
        decreaseCount() {
          if (this.count > this.minCount) {
            this.count--
          }
        }
      }
  }
</script>

<style scoped>
  .home__inner {
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .inputCount {
    height: 28px;
    text-align: center;
    padding: 0 5px;
    border: 1px solid #000;
    border-radius: 3px;
    margin: 0 10px;
  }
  .Button {
    width: 30px;
    height: 30px;
    cursor: pointer;
    outline: none;
    font-size: 20px;
    border: 1px solid #000;
    border-radius: 3px;
    padding: 0;
  }
</style>
