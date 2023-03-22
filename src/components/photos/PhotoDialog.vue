<template>
  <v-dialog
    v-model="dialogVisible"
    max-width="600"
  >
    <v-card>
      <v-card-title>{{ photo.title }}</v-card-title>
      <v-card-text>
        <v-img 
          :src="photo.url"
        ></v-img>
      </v-card-text>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  name: 'ThePhotoDialog',
  data: () => ({
    dialogVisible: false,
    photo: {}
  }),
  methods: {
    openDialog(photo) {
      this.photo = photo
      this.dialogVisible = true
    }
    
  }
}
</script>