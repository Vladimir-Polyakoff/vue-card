<template>
  <v-container>
    <PhotosForm @addPhoto="addPhoto"></PhotosForm>
    <v-row>
      <!-- :obj="photo" @changeTitle="changeTitlePar" -->
      <Photo v-for="photo in photos" 
        :key="photo.id"
        :photo="photo" 
        @openPhoto="openPhoto">
      </Photo>
    </v-row> 
    <PhotoDialog ref="PhotoDialog"></PhotoDialog>
  </v-container>
</template>

<script>
import Photo from '@/components/photos/Photo'
import PhotosForm from '@/components/photos/PhotoForm'
import PhotoDialog from '@/components/photos/PhotoDialog'

export default {
  components: {
    Photo,
    PhotosForm,
    PhotoDialog
  },
  data: () => ({
    photos: [],
    currentPhoto: {},
    dialogVisible: false
  }),
mounted() {
  this.fetchTodo()
},
methods: {
  fetchTodo() {
    this.axios.get(`https://jsonplaceholder.typicode.com/photos?_limit=10`)
      .then(response => this.photos = response.data)
  },
  addPhoto(photo) {
    this.photos.push(photo)
  },
  openPhoto(photo) {
    // this.currentPhoto = photo
    // this.dialogVisible = true
    this.$refs.PhotoDialog.openDialog(photo)
    console.log(this.dialogVisible);
  }

}
  
  // methods: {
  //   changeTitlePar({id, newTitle}){
  //     this.photos.forEach((el, index) => {
  //       if(el.id == id) {
  //         this.photos[index].title = newTitle
  //       }
  //     })
  //   }
  //  }
  }
</script>
