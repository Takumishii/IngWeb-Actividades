<template>
<div>
<p>{{ mensaje }}</p>
</div>
</template>
<script>
export default {
  name: "Hijo",
  props: ['mensaje']
}
</script>