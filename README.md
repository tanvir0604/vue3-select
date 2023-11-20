# vue3-select

> A vue3 component to create a searchable select menu
## Getting Started

These instructions will help you to install the package on your local machine and create a server side pagination system in a minute.

## Installation

installation process is very simple:

```sh
$ cd VUE3PROJECT
$ npm i @shafkat/vue3-select
```

## Usage

### Import the component

```sh
$ import { Select } from "@shafkat/vue3-select";
$ import "~@shafkat/vue3-select/dist/style.css"
```

### Use the component

```sh
$ <Select :options="options" v-model="value"></Select>
```

## API

#### Props

| Name       | Type   | Default | Details                                                 |
|------------|--------|---------|---------------------------------------------------------|
| options    | Array  | []      | Required - A list of data to generate the options       |
| class-name | String | NULL    | Optional - Change the css design according to your need |

Example:

```tsx
<script setup>
    import { ref } from "vue";
    import { Select } from "@shafkat/vue3-select";
    let options = ref([
        {name: "Atlantic", value: "A"},
        {name: "Atlantica", value: "B"},
        {name: "Cat", value: "C"},
        {name: "Catarpillar", value: "D"},
        {name: "Elephant", value: "E"},
        {name: "Elephant nose", value: "F"}
    ]);
    let value = ref("C");
</script>
<template>
    <div class="col-md-6 offset-md-3">
        <form>
            <fieldset>
                <legend>Disabled fieldset example</legend>
                <div class="mb-3">
                    <label for="textInput" class="form-label">Input</label>
                    <input type="text" id="textInput" class="form-control" placeholder="Input">
                </div>
                <div class="mb-3">
                    <label for="select" class="form-label">Select menu</label>
                    <Select :options="options" v-model="value"></Select>
                </div>
                <button type="submit" class="btn btn-primary">Submit</button>
            </fieldset>
        </form>
    </div>
</template>
<style scoped>
</style>

```

> include bootstrap >= 5.0 for styling


## Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct, and the process for submitting pull requests to us.

1.  Fork it!
2.  Create your feature branch: `git checkout -b my-new-feature`
3.  Add your changes: `git add .`
4.  Commit your changes: `git commit -am 'Add some feature'`
5.  Push to the branch: `git push origin my-new-feature`
6.  Submit a pull request :sunglasses:

## Versioning

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/tanvir0604/vue3-select/tags).

## Authors

* **Md Shafkat Hussain Tanvir** - *Initial work* - [tanvir](https://github.com/tanvir0604)

See also the list of [contributors](https://github.com/tanvir0604/vue3-select/contributors) who participated in this project.