<template>
  <div class="hello">
    <h1> UUID converter </h1>
    <p>
      Convert UUID 32 characters representation UUID to HEX base representation
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-cli documentation</a>.
    </p>
    <label>
      Type uuid here
      <input v-model="uuid32Char" placeholder="1eaf76d9-dfe0-63f0-80ad-005056a3ab03" >
    </label>
    <hr>
    <label>
      The HEX representation
      <input v-model="uuid16Char" placeholder="1EAF76D9-DFE0-63F0-80AD-005056A3AB03">
    </label>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      uuid32Char: '',
    }
  },
  computed: {
    uuid16Char:{
      get() {
        let uuid = this.uuid32Char || '';
        uuid = uuid.toUpperCase();
        uuid = uuid.replace(/ /g, '');
        return uuid;
      },
      set(value){
        if (value instanceof String && value.length === 32) {
          let uuid32='';
          uuid32 += value.substring(0, 8) + '-';
          uuid32 += value.substring(8, 4) + '-';
          uuid32 += value.substring(12, 4) + '-';
          uuid32 += value.substring(16, 4) + '-';
          uuid32 += value.substring(20, 12);
          this.uuid32Char = uuid32;
        }

      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
input {
  width: 300px;
}
</style>
