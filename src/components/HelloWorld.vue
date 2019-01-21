<template>
  <div>
    <h1>{{ msg }}</h1>
    <input type="file" accept=".json" @change="getFile"/>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  methods: {
    getFile (e) {
      var reader = new FileReader()
      reader.readAsDataURL(e.srcElement.files[0])
      reader.onload = () => {

        // eslint-disable-next-line
        console.log(JSON.parse(window.atob(reader.result.split(',')[1])))
      }
    }
  }
}
</script>
