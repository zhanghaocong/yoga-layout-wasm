# yoga-layout-wasm
> yoga-layout webassembly module, for browser and node. fallback to asm.js in non-webassembly environment

## Get Start

```
$ npm i yoga-layout-wasm --save
```

``` javascript
import Yoga from 'yoga-layout-wasm'

function test (yoga) {
  const Node = yoga.Node
  const root = Node.create();
  root.setWidth(500);
  root.setHeight(300);
  root.setJustifyContent(yoga.JUSTIFY_CENTER);
  
  const node1 = Node.create();
  node1.setWidth(100);
  node1.setHeight(100);
  
  const node2 = Node.create();
  node2.setWidth(100);
  node2.setHeight(100);
  
  root.insertChild(node1, 0);
  root.insertChild(node2, 1);
  
  root.calculateLayout(500, 300, yoga.DIRECTION_LTR);
  console.log(root.getComputedLayout());
  // {left: 0, top: 0, width: 500, height: 300}
  console.log(node1.getComputedLayout());
  // {left: 150, top: 0, width: 100, height: 100}
  console.log(node2.getComputedLayout());
  // {left: 250, top: 0, width: 100, height: 100}
}

const urlToWasmFolder = 'node_modules/yoga-layout-wasm/dist/'

Yoga(urlToWasmFolder).then(test)
```

## Examples

```
$ npm run example:node
$ npm run example:html
```