<template>
  <div class="header">
    <h1>
      Helveti<span>calc</span>
    </h1>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
  }
}
</script>

<style scoped>
.header {
  max-width: 600px;
  margin: 0 auto;
  padding: 0;
  color: #333;
  font-size: 3em;
  font-weight: bold;

  -moz-user-select:none;
  -webkit-user-select:none;
  -webkit-touch-callout:none;
  -ms-user-select:none;
  user-select:none;
}

/* Prevents font overflowing right on small screens */
@media (max-width:600px) {
  .header {
    font-size: 9vw;
  }
}

.header h1 {
  margin: 0;
  padding: 0;
}

.header span {
  color: orange;
}

</style>
