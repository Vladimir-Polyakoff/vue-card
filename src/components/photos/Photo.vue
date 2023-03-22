<template>
  <v-col cols="4">
    <v-card @click="openPhoto">
      <v-card-title>{{ photo.title }}</v-card-title>
      <v-card-text>
        <v-img
          width="200"
          height="200"
          :src="photo.url"
        />
      </v-card-text>
    </v-card>
  </v-col>
</template>

<script>
  export default {
    name: 'ThePhoto',
    props: {
      photo: {
        type: Object,
        required: true
      }
    //   obj: {
    //     type: Object,
    //     required: true
    //   }
    },
      methods: {
        openPhoto() {
          this.$emit('openPhoto', this.photo)
        }
      }
    // created() {
    //   this.changeTitle()
    // },
    // methods: {
    //   changeTitle() {
    //     Number(this.obj.id) % 2 
    //       ? this.$emit('changeTitle', {id: this.obj.id, newTitle: 'НЕ четный'})
    //       : this.$emit('changeTitle', {id: this.obj.id, newTitle: 'четный'})
    // } 
    // }
  }
</script>
