<template>
  <div class="card">
    <header class="card-header">
      <p class="card-header-title">
        Protocol
      </p>
    </header>
    <div class="card-content">
      <p>
        <strong>P2P protocol version: </strong>  {{ protocol.p2p }}
      </p>
      <p>
        <strong>Block protocol version: </strong>  {{ protocol.block }}
      </p>
      <p>
        <strong>App protocol version: </strong> {{ protocol.app }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    protocol: {
      type: Object,
      required: true
    }
  }
}
</script>
