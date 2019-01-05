<template>
  <section class="section">
    <div class="card">
      <header class="card-header">
        <p class="card-header-title">
          Node info
        </p>
      </header>

      <div class="card-content">
        <div class="columns">
          <div class="column">
            <p>
              <strong>ID</strong>: {{ node_info.id }}
            </p>
            <p>
              <strong>Listen address</strong>: {{ node_info.listen_addr }}
            </p>
            <p>
              <strong>Network</strong>: {{ node_info.network }}
            </p>
            <p>
              <strong>Channels</strong>: {{ node_info.channels }}
            </p>
            <p>
              <strong>Moniker</strong>: {{ node_info.moniker }}
            </p>
            <p>
              <strong>TX Index</strong>: {{ node_info.other.tx_index }}
            </p>
            <p>
              <strong>RPC Address</strong>: {{ node_info.other.rpc_address }}
            </p>
          </div>
          <div class="column">
            <protocol-info :protocol="node_info.protocol_version" />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import ProtocolInfo from '@/components/ProtocolInfo'

export default {
  components: {
    ProtocolInfo
  },

  data() {
    return {
      node_info: {
        protocol_version: {
          p2p: '',
          block: '',
          app: ''
        },
        id: '',
        listen_addr: '',
        network: '',
        version: '',
        channels: '',
        moniker: '',
        other: {
          tx_index: '',
          rpc_address: ''
        }
      },
      sync_info: {
        latest_block_hash: '',
        latest_app_hash: '',
        latest_block_height: '',
        latest_block_time: '',
        catching_up: false
      },
      validator_info: {
        address: '',
        pub_key: {
          type: '',
          value: ''
        },
        voting_power: ''
      }
    }
  },

  async mounted() {
    const { result } = await this.$axios.$get('/api/status')

    this.node_info = result.node_info
    this.sync_info = result.sync_info
    this.validator_info = result.validator_info
  }
}
</script>
