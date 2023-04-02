<template>
  <div class="header">
    <div class="header__wrap">
      <div class="header__wrap-text">USERS</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HeaderItem',
}
</script>

<style scoped>
.header {
  position: absolute;
  top: 0;
  left: 0;
  height: 77px;
  width: 100%;
  background-color: #ffffff;
}

.header__wrap {
  display: flex;
  flex-direction: row;
  align-items: center;
  height: 100%;
  padding-left: 51px;
  border-bottom: 1px solid rgba(114, 114, 112, .2);
  font-size: 20px;
  line-height: 23px;
}
</style>
