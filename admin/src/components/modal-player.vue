<template>
  <div id="player-modal" class="modal" tabindex="-1" role="dialog" >
    <div class="modal-dialog modal-lg" role="document">
      <div class="modal-content">
        <div class="modal-body">
          <player v-bind:player-id="'modal-player-div'"
                  ref="player"></player>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import Player from "./player";
export default {
  name: 'modal-player',
  components: {Player},
  data: function () {
    return {
      aliPlayer: {}, // 播放器实例
    }
  },
  mounted() {
    let _this = this;
    // 当关闭模态框时，暂停播放
    $('#player-modal').on('hidden.bs.modal', function (e) {
      _this.$refs.player.pause();
    })
  },
  methods: {
    playUrl(url) {
      let _this = this;
      _this.$refs.player.playUrl(url);
    },

    playVod(vod) {
      let _this = this;
      _this.$refs.player.playVod(vod);
      $("#player-modal").modal("show");
    },

  }
}
</script>

<style scoped>
#player-modal .modal-body {
  padding: 0;
}

</style>