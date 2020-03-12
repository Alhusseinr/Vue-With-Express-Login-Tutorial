<temnplate>
  <div>
    <h2>Dashboard</h2>
    <p>Name: {{user.name}}</p>
  </div>
</temnplate>

<script>
import axios from 'axios'
import router from '../router'

export default {
  name: 'dashboard',
  data () {
    return {
      user: {
        name: 'Rami'
      }
    }
  },
  methods: {
    getUserData: function () {
      let self = this
      axios
        .get('/api/user')
        .then((res) => {
          console.log(res)
          self.$set(this, 'user', res.data.user)
        })
        .catch((e) => {
          console.log(e)
          router.push('/')
        })
    }
  },
  mounted () {
    this.getUserData()
  }
}
</script>
