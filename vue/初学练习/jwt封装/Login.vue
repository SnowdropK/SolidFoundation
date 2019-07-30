export default {
  name: 'Login',
  data() {
    return {
      username: '',
      password: '',
    }
  },
  methods: {
    onLogin() {
      const { username, password } = this
      const data = {
        username,
        password
      }

      this.$http.post('url', data)
        .then(res => {
         // 登录成功
          if(res.token) {
            // 储存 token
            localStorage.token = res.token
          }
        })
        .catch(error => {
          // 登录失败
          // 验证后端返回的错误字段，如果匹配，提示用户
          // axios 配置里必须要 return Promise.reject(error.response.data) 才能拿到错误字段
          if(error.xxx == 'xxx') {
            alert('用户名或密码错误！')
          }
        })
    }
  }
}
