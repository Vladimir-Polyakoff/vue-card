<template>
  <div class="w-140 mx-auto">
    <v-text-field
        v-model="percent"
        label="First name"
    ></v-text-field>

    <div>
      <div class="text-caption">
        Сумма
      </div>
      <v-slider
        v-model="ammount"
        :step="1000" 
        :min="1000" 
        :max="30000"
        :thumb-size="36"
        thumb-label="always"
      ></v-slider>
    </div>

    <div>
      <div class="text-caption">
        Срок
      </div>
      <v-slider
        v-model="term"
        :step="1" 
        :min="5" 
        :max="30"
        :thumb-size="36"
        thumb-label="always"
      ></v-slider>
    </div>
    <div class="result">{{ result }}</div>
  </div>
</template>

<script>
export default {
  name: 'TheMain',

  data () {
    return {
      percent: 0.01,
      ammount: 6000,
      term: 12,
      list: [
        {
          alesha: 'звонит маме?'
        },
        {
          volod: 'звонит маме?'
        },
        {
          sasha: 'звонит маме?'
        },
        {
          papa: 'звонит маме?'
        }
      ]
    }
  },

  computed: {
    result () {
      console.log(this.percent)
      return this.ammount + this.ammount * this.percent * this.term
    }
  },

  created () {
    console.log(this.isHasSubstring('AAAacbccabc', 'cb'))
  },

  methods: {
  // 1) вернуть "a-5 d-3 s-1" пофиг на ШРИФТ
  //   hasLatter (str) {
  //     const res = {}
  //     let string = ''
  
  //     for(let i = 0; i < str.length; ++i) {
  //       if (!res[str[i]]) {
  //         res[str[i].toLowerCase()] = 1
  //       } else {
  //         res[str[i]]++
  //       }
  //     }

  //     for(const key in res) {
  //       string += `${key}-${res[key]} `
  //     }

  //     return string
  //   }
  // }

  //   hasLatter (str) {
  //     let temp = str[0]
  //     let resStr = ''
  //     let count = 0

  //     for(let i = 0; i < str.length + 1; ++i) {
  //       if (temp === str[i]) {
  //         count++
  //       } else {
  //         resStr += ` ${temp}-${count}`
  //         temp = str[i]
  //         count = 1
  //       }
  //     }
  //     // resStr += ` ${temp}-${count}`

  //     return resStr
  //   }
  // }

// 'AAAacbccabc', 'ab'

    isHasSubstring (str, subStr) {
      let temp = ''
      let j = 0

      for (let i = 0; i < str.length; i++) {
        if (str[i] === subStr[j]) {
          temp += str[i]
          j++

          if (temp === subStr) {
            return true
          }
        } else {
          temp = ''
          j = 0
        }
      }

      return false
    }
  }
}  
</script>

<style scoped>
  .result {
    color: red;
  }
</style>
