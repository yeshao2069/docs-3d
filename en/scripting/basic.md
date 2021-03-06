## Operating environment

The APIs for the __Cocos Creator 3D__ engine all exist in the module `cc`. They can be imported it using standard ES6 module import syntax. Example:

```ts
import {
    Component, // Import class Component
    _decorator, // mport namespace _decorator
} from "cc";
import * as cc from "cc"; // Import the entire Cocos Creator 3D module as a namespace Cocos Creator 3D

@_decorator.ccclass("MyComponent")
export class MyComponent extends Component {
    public v = new cc.Vec3();
}
```

## Reserved identifier `cc`

Due to historical reasons, `cc` is an identifier reserved for __Cocos Creator 3D__. Its behavior is *equivalent to* having defined an object named `cc` at the top of any module. Therefore, developers should not use `cc` as the name of any **global** object. Example:

```ts
/* const cc = {}; // Every Cocos Creator 3D script is equivalent to an implicit definition here */

import * as cc from "cc"; // Error: Namespace import name cc is reserved by Cocos Creator 3D

const cc = { x: 0 };
console.log(cc.x); // Error: The global object name cc is reserved by Cocos Creator 3D

function f () {
    const cc = { x: 0 };
    console.log(cc.x); // Correct: cc can be used as the name of a local object

    const o = { cc: 0 };
    console.log(o.cc); // Correct: cc can be used as a property name
}

console.log(cc, typeof cc); // error: behavior is undefined
```