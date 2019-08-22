<template>
  <div id="select">
  <select :options="options" label="title">
    <option v-for="(option,i) in options" :key="i" :value="option">
                <i :style="'background:'+option.variation[0] "/>
                {{ option[i].title }}
            </option>
  </select>
</div>
</template>

<script>
export default {
    data(){
        return {
        options: [
          {
              title: 'Read the Docs',
              icon: 'fa-book',
              url: 'https://codeclimate.com/github/sagalbot/vue-select'
            },
            {
              title: 'View on GitHub',
              icon: 'fa-github',
              url: 'https://codeclimate.com/github/sagalbot/vue-select'
            },
            {
              title: 'View on NPM',
              icon: 'fa-database',
              url: 'https://codeclimate.com/github/sagalbot/vue-select'
            },
            {
              title: 'View Codepen Examples',
              icon: 'fa-pencil',
              url: 'https://codeclimate.com/github/sagalbot/vue-select'
            }
        ]
      }
    }
}
</script>

<style>
body {
  font-family: "Source Sans Pro", "Helvetica Neue", Arial, sans-serif;
}

h1,.muted {
  color: #2c3e5099;
}

h1 {
  font-size: 26px;
  font-weight: 600;
  text-rendering: optimizelegibility;
  -moz-osx-font-smoothing: grayscale;
  -moz-text-size-adjust: none;
}

#select {
  max-width: 30em;
  margin: 1em auto;
}

#select .dropdown li {
  border-bottom: 1px solid rgba(112, 128, 144, 0.1)
}

#select .dropdown li:last-child {
  border-bottom: none;
}

#select .dropdown li a {
  padding: 10px 20px;
  display: flex;
  width: 100%;
  align-items: center;
  font-size: 1.25em;
}

#select .dropdown li a .fa {
  padding-right: 0.5em;
}
</style>