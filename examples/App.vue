<template>
  <div>
    <nav class="navbar navbar-expand-lg navbar navbar-dark bg-dark shadow-sm mb-3">
      <span class="navbar-brand mb-0">Vue.js jQuery Mask Demo</span>
      <ul class="navbar-nav ml-auto">
        <li class="nav-item">
          <a class="nav-link" href="https://github.com/ankurk91/vue-jquery-mask"
             target="_blank"> GitHub</a></li>
      </ul>
    </nav>

    <main class="container">
      <div class="row">
        <div class="col-md-8 mb-3">

          <section class="card mb-3">
            <div class="card-body">
              <form class="form-inline">
                <button type="button" class="btn btn-secondary mr-2" @click.prevent="setNewValue()">
                  Set new value pragmatically
                </button>
              </form>
            </div>
          </section>

          <form class="card card-body" method="post" action="/" @submit.prevent="submit()">

            <div class="form-group">
              <label>Enter phone number</label>
              <vue-mask class="form-control" v-model="form.phoneNumber" mask="00-00000-00000"></vue-mask>
              <span class="form-text text-muted small">
              {{form.phoneNumber}}
            </span>
            </div>

            <div class="form-group">
              <label>Enter date (<code>raw:false</code>)</label>
              <vue-mask class="form-control"
                        v-model="form.date"
                        mask="00/00/0000"
                        :raw="false"
                        :options="options.date"
                        name="date"
              ></vue-mask>
              <span class="form-text text-muted small">
              {{form.date}}
            </span>
            </div>

            <div class="form-group" >
              <label>Money</label>
              <vue-mask v-model="form.money"
                        mask="#.##0,00"
                        :options="options.money"
                        name="money"
                        class="form-control"
              ></vue-mask>
              <span class="form-text text-muted small">
              {{form.money}}
            </span>
            </div>

            <hr>

            <div class="form-group">
              <button class="btn btn-primary" type="submit"><i class="glyphicon glyphicon-ok"></i> Submit form
              </button>
            </div>

          </form>
        </div>

        <aside class="col-md-4 mb-3">
          <div class="card">
            <div class="card-header"> Links</div>
            <div class="card-body">
              <ul>
                <li><a href="https://github.com/ankurk91/vue-jquery-mask" target="_blank">Github</a></li>
                <li><a href="https://www.npmjs.com/package/vue-jquery-mask" target="_blank">npm</a></li>
                <li><a href="https://github.com/igorescobar/jQuery-Mask-Plugin" target="_blank">
                  jQuery-Mask-Plugin
                </a></li>
              </ul>
            </div>
          </div>
        </aside>
      </div>
    </main>
    <footer class="text-center text-muted small mb-3">
      Created by <a href="https://twitter.com/ankurk91" target="_blank" rel="noopener">@ankurk91</a>
    </footer>
  </div>
</template>

<script>
  import Vue from 'vue';

  import vueMask from '../src/index';

  export default {
    name: 'app',
    data() {
      return {
        form: {
          phoneNumber: 123456789,
          date: null,
          money: null
        },
        options: {
          date: {
            onChange: this.onChangeDate,
            placeholder: '__/__/____',
            clearIfNotMatch: true
          },
          money: {
            reverse: true,
            selectOnFocus: true
          }
        },
      }
    },
    components: {
      vueMask
    },
    methods: {
      submit() {
        console.log('Form submit event', this.form);
      },
      setNewValue() {
        console.log('Set new phone value');
        this.form.phoneNumber = '919800123456';
      },
      onChangeDate(val, e) {
        console.log('onChangeDate - ', val, e)
      }
    },
  }
</script>
