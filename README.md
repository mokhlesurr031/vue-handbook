# vue-handbook

# Vue by CLI

## Install vue
```
sudo npm install -g @vue/cli
```


## Check version 
```
vue --version 
```

## Create app 
```
sudo vue create project-name 
```

## Run project 
```
cd app-name 
sudo npm run serve
```


## .Vue file
A *.vue file is a custome file format that uses HTML-like syntax to describe a portion of the UI.
.vue file consists of three types of top-level language block
```
<template></template> -HTML of the UI
<script></script> - Data and logic functionalities
<style></style> - CSS block 
```


## Components 
A .vue file is called a single file component(SFC)


## Might not get delete permission 
sudo chown -R username:groupname project-name

## Project Structure
1. package.json - Contains dependencies and scripts(serve, build, lint) required for the project.
2. package-lock.json - Ensures consistent installation of the dependencies. 
3. babel.config.js - Babel configuration file. Its a tool that transform modern js features being used in development code into older syntax that is more cross browser compatible in production code. 
4. node_modules - Where all the dependencies are installed. 
5. public - Contains static assets that are published when we want to live with our application. It containes index.html that we should never modify only except the title. 
6. src - Where we will be building and writing code for our application. 

***src structure***
  ```
  src(folder)
  ├── App.vue - Where we specify html, css and js code and is mounted to main.js.
  ├── assets
  │   └── logo.png
  ├── components
  │   └── HelloWorld.vue - Component to be rendered by App.vue.
  └── main.js - Starting point of our vue application.

  3 directories, 4 files
  ```


## Component Skeleton

```
<template>
  <div></div>
  <div></div>
</template>

<script>
  export default{
    name: "App",
  };

</script>

<style>
</style>
```

## Lets Start Practicing and Learning
Lets delete the **components** folder.

Also delete the HelloWorld related code from the App.vue.

For now we are going to learn 'template-syntax'.


Lets display the a simple name from App.vue.

```
App.vue
---------
<template>
  <div>{{name}}</div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      name: "mahin"
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

```

## Binding Text 

```
<template>
  <div>{{greet}} {{name}}</div>
</template>

<script>
  export default{
    name: "App", 
    data(){
      return{
        greet: "Hello",
        name: "Mahin",
      };
    },
  };
</script>

<style>
</style>
```

## Text-Binding using v-text Directives(rerely used)
```
<template>
  <div v-text="greet"/>
</template>

<script>
  export default{
    name: "App", 
    data(){
      return{
        greet: "Hello",
      };
    },
  };
</script>
```






## Binding HTML

```
<template>
  <div v-html="greet"/>
  <div v-html="hack"/>
</template>

<script>
  export default{
    name: "App", 
    data(){
      return{
        greet: "<b>Hello</b>",
        hack: `<a href='#' onclick="alert('Nothing')">Click Link</a>`,
      };
    },
  };
</script>

<style>
</style>
```

## Binding to Attributes 

Its possible to bind data to attributes such as id, class, style and even boolean. 

```
<template>
  <div v-bind:id="headingId">Heading</div>
  <button v-bind:disabled="idDisabled">Click Me</button>
</template>

<script>
  export default{
    name: "App", 
    data(){
      return{
        headingId: "heading",
        idDisabled: true,
      };
    },
  };
</script>
```

## Binding Class

```
<template>
  <div class="underline">Underline Text</div>
  <div v-bind:class="status">Status</div>
  <div v-bind:class="status" class="underline">Both Binding</div>
  <div v-bind:class="isPromoted && 'italic'">Italic with AND binding</div>
  <div v-bind:class="isSoldOut ? 'sold-out': 'new'">Ternary Operator, if sold out show red else green</div>
  <div v-bind:class="['new', 'italic']">List Binding</div>

</template>

<script>
  export default{
    name: "App", 
    data(){
      return{
        status: "danger",
        isPromoted: true,
        isSoldOut: true
      };
    },

  };
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.underline{
  text-decoration: underline;
}
.italic{
  font-style: italic;
}
.new{
  color: green;
}
.sold-out{
  color: red;
}
</style>

```

## Binding Style

First Approach

```
<template>
  <div v-bind:style="{
    color: highlightColor,
    'font-size': headerSize + 'px'
  }">First Approach</div>

  <div v-bind:style="{
    color: highlightColor,
    fontSize: headerSize + 'px',
    padding: padding
  }">Second Approach</div>

</template>

<script>
  export default{
    name: "App", 
    data(){
      return{
        highlightColor: "orange",
        headerSize: 50,
        padding: '20px'
      };
    },

  };
</script>
```

Second Approach

```
<template>
  <div v-bind:style="styleObject">First Approach</div>
</template>

<script>
  export default{
    name: "App", 
    data(){
      return{
        styleObject: {
          color: "orange",
          fontSize: '50px',
          padding: '20px'
        }
      };
    },

  };
</script>
```
or
```
<template>
  <div v-bind:style="[styleObject, anotherObject]">First Approach</div>
</template>

<script>
  export default{
    name: "App", 
    data(){
      return{
        styleObject: {
          color: "orange",
          fontSize: '50px',
          padding: '20px'
        },
        anotherObject: {
          backgroundColor: 'lightgreen',
        }
      };
    },

  };
</script>
```

## v-bind Shorthand
As v-bind is a frequently used syntax. We can skip this and keep the code simpler using only **:attr**.

```
<template>
  <div :style="[styleObject, anotherObject]">First Approach</div>
</template>

<script>
  export default{
    name: "App", 
    data(){
      return{
        styleObject: {
          color: "orange",
          fontSize: '50px',
          padding: '20px'
        },
        anotherObject: {
          backgroundColor: 'lightgreen',
        }
      };
    },

  };
</script>
```

## Conditional Rendering

There are 4 conditional directives. 

1. v-if
2. v-else
3. v-else-if
4. v-show

```
<template>
  <h2 v-if="num==0">The number is zero</h2>
  <h2 v-else-if="num==5">The number is five</h2>
  <h2 v-else>The number is not zero</h2>

</template>

<script>
  export default{
    name: "App", 
    data(){
      return{
        num: 5,
      };
    },

  };
</script>
```

## List Rendering
## Lists and keys 
## Methods 
## Event Handling 
## Form Handling 
## Modifier 
## Directives 
## Computed Properties vs Methods 
## Computer Properties vs v-for 
## Computed Setter 
## Watchers 
## Immediate and Deep Watchers 
## Components 
## Component Props 
## Prop Types and Validations 
## Non-Prop Attributes 
## Provide and Inject 
## Component Events 
## Validation Emmited Events 
## Components and v-model 
## Slots 
## Named Slots 
## Slot Props 
## Component Styles 
## Dynamic Components 
## Keeping Dynamic Components Alive 
## Teleport Component 
## HTTP and Vue
## HTTP GET Request 
## HTTP POST Request 
## Lifecycle Hooks 
## GET Request on Page Load 
## Template Refs
## Reusability with Mixins 
## Composition API
## Replacing Data with Refs
## Replacing Data with Reactive 
## Reactivity and toRefs
## Replacing Methods 
## v-model and Composition API
## Replacing Computed Properties 
## Replacing Watchers 
## Replacing Provide/Inject 
## Replacing Lifcycle Hooks 
## Template Refs and Composition API
## Props and Composition API
## Custom Events and Composition API 
## Deploying Vue Applications
