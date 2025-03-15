<script>
import { mapGetters } from 'vuex';

export default {
  computed: {
    ...mapGetters({
      notificationMetadata: 'notifications/getMeta',
    }),
    unreadCount() {
      if (!this.notificationMetadata.unreadCount) {
        return '';
      }

      return this.notificationMetadata.unreadCount < 100
        ? `${this.notificationMetadata.unreadCount}`
        : '99+';
    },
    isNotificationPanelActive() {
      return this.$route.name === 'notifications_index';
    },
  },
  methods: {
    openNotificationPanel() {
      if (this.$route.name !== 'notifications_index') {
        this.$emit('openNotificationPanel');
      }
    },
  },
};
</script>

<template></template>
