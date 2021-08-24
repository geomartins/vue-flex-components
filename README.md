# Vue-Flex-Components

Vue-flex-components is a vue library that consist of various vue custom components such as LoadingContainer, InnerLoadingContainer, FloatingActionButton

## Installation
#### Via npm 

```sh
npm install vue-flex-components
```

## Usuage
```javascript
import FlexLoading from "vue-flex-components";
export default defineComponent({
  components: {
    FlexLoading,
  },
  data() {
    return {
      visible: true,
    };
  },
});

```


## Example
```javascript
<div>
    <flex-loading
      label="Pls Wait while we process ur transaction ..."
      labelColor="teal"
      labelSize="1.1rem"
      labelWeight="bold"
      bgColor="#80808014"
      iconColor="red"
      icon="fas fa-spinner"
      iconSize="50px"
      :showing="visible"
      speed="6s"
      transition="4s"
    >
      Anything goes inside here .....................
    </flex-loading>

    <div
      @click="visible = !visible"
      style="position: absolute; z-index: 500000000; top: 0px"
    >
      Toggle Now
    </div>
```

## License

MIT

**Free Software, Hell Yeah!**
