<template>
  <div class="container">
    <div class="section links">
      <Nav />
    </div>
    <div class="section tribute">
      <h1 class="title">In Loving Memory<br/>愛的回憶</h1>
      <img height="292" src="~/assets/frontimage.jpg" alt="In loving memory 愛的回憶" />
      <div class="subtitle"><div class="name">{{ $config.name }} {{ $config.name_zh }}</div>{{ $config.dates }}<br/>民國四十四年十一月二十三日至一百一十年七月十五日</div>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style lang="scss">

</style>
