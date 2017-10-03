<template>
  <v-layout>
    <v-card contextual-style="dark">
      <span slot="header">
        My Account
      </span>
      <div slot="body">
        <table class="table table-striped">
          <thead>
            <tr>
              <th>
                First Name
              </th>
              <th>
                Last Name
              </th>
              <th>
                Email
              </th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>
                {{$store.state.account.firstName}}
              </td>
              <td>
                {{$store.state.account.lastName}}
              </td>
              <td>
                {{$store.state.account.email}}
              </td>
            </tr>
          </tbody>
        </table>
      </div>
      <div slot="footer">
        Made with love by Vivid Web
      </div>
    </v-card>
  </v-layout>
</template>

<script>

import VLayout from '@/layouts/Default';
import VCard from '@/components/Card';
import Axios from 'axios';
export default {
  /**
   * The name of the page.
   */
  name: 'account-index',
  data() {
    return {
      data: {
        name: '',
        age: '',
        email: ''
      }
    }
  },
  mounted() {
    this.getinfo();
  },
  methods: {
    getinfo() {
      Axios.get('http://rapapi.org/mockjsdata/20947/requestQ', {
        params: {
          q: "12"
        }
      })
        .then(function(response) {
          console.log(response);
        })
        .catch(function(err) {
          console.log(err);
        });

    }

  },
  /**
   * The components that the page can use.
   */
  components: {
    VLayout,
    VCard,
    Axios
  },
};
</script>
