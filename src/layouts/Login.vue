<template>
  <d-container>
    <div style="text-align: center;" class="align-center">
      <img style="width: 120px; margin-top: 60px; margin-bottom: 20px" src="@/assets/images/gorse.png"/>
      <h5>欢迎使用协同过滤推荐系统</h5>
      <d-card>
        <d-card-body>
          <d-form method="post" action="/login">
            <label class="sr-only" for="username">用户名</label>
            <d-form-input id="username" name="user_name" class="mb-1" placeholder="Username" />
            <label class="sr-only" for="password">密码</label>
            <d-form-input id="password" name="password" class="mt-2" type="password" placeholder="Password" />
            <d-alert v-if="this.$route.query.msg === 'incorrect'" theme="danger" class="mt-2"
                     :show="timeUntilDismissed"
                     @alert-dismissed="timeUntilDismissed = 0"
                     @alert-dismiss-countdown="handleTimeChange">用户名或密码错误</d-alert>
            <d-button class="mt-2" theme="primary" type="submit">登录</d-button>
          </d-form>
        </d-card-body>
      </d-card>
    </div>
  </d-container>
</template>

<style>
.align-center {
  margin: auto;
  max-width: 480px;
}
</style>

<script>
export default {
  data() {
    return {
      timeUntilDismissed: 5,
    };
  },
  methods: {
    handleTimeChange(time) {
      this.timeUntilDismissed = time;
    },
  },
};
</script>
