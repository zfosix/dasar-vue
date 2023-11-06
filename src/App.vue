<template>
  <div>
    <p>-----------Templating----------</p>
    {{ nama }}
    {{ number }}
    <div v-html="kelas"></div>

    <p>-----------Data Binding----------</p>
    <button :disabled="nonatif">Button</button>
    <h1 v-bind="property">Jar</h1>
    <input :type="typeInput">

    <p>-----------Data Binding----------</p>
    {{ count === 0 ? count + 1 : count + 2 }}
    <p>-----------v-if----------</p>
    <button v-if="show">Submit</button>
    <div v-if="count === 1">
      number 1
    </div>
    <div v-else-if="count === 2">
      number 2
    </div>
    <div v-else>
      number lebih dari 2
    </div>
    <p>-----------computed dan methods----------</p>
    <button @click="counterNumber">methods {{ counterButton }}</button>
    <button @click="counterComputed">computed {{ numberComputed }}</button>
    <input :type="typeInput">
    <button @click="showPassword">Show Password</button>

    <p>-----------class dan style----------</p>
    <ul>
      <li :class="[
        'fs',
        { active: isActive },
        { fs40px: isActive }
      ]">
        Lanjut
      </li>
    </ul>
    <button @click="ubahWarna">Ubah Warna</button>

    <p>-----------list rendering----------</p>
    <ul>
      <li v-for="(item, index) in daftarKelas" :key="index">
        {{ index + 1 }} {{ item }}
      </li>
    </ul>
    <p>-----------v mode----------</p>
    <input type="text" v-model="inputKelas">
    {{ inputKelas }}

  </div>
</template>

<script>
export default {
  data() {
    return {
      inputKelas: '',
      daftarKelas: ['RPL 1', 'RPL 2', 'RPL 3'],
      counterButton: 0,
      numberComputed: 0,
      show: true,
      count: 1,
      nama: 'Fajar',
      number: 6,
      kelas: '<h1>kelas 11</h1>',
      nonatif: true,
      property: {
        id: 1,
        class: 'color'
      },
      isActive: true
    }
  },
  methods: {
    counterNumber() {
      this.counterButton += 1;
    },
    showPassword() {
      if (this.typeInput == 'password') {
        this.typeInput = 'text';
      } else {
        this.typeInput = 'password';
      }
    },
    ubahWarna() {
      if (this.isActive) {
        this.isActive = false;
      } else {
        this.isActive = true;
      }
    }
  },
  computed: {
    numberComputed() {
      return this.counterButton * 6;
    }
  }
}
</script>

<style>
.color
{
  color: red;
}

.fs40px
{
  font-size: 40px;
}

.active
{
  color: blue;
}
</style>
