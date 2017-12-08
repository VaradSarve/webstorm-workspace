# Issue

[![Greenkeeper badge](https://badges.greenkeeper.io/tusharmath/webstorm-workspace.svg)](https://greenkeeper.io/)
Webstorm doesn't properly import local packages from `node_modules` directory instead imports using relative paths.

# Steps to reproduce

0. Clone this repository
0. Run `yarn`
0. Open `foo/index.ts` try to import an exported property from `bar`.

    ```ts
    import {bear} from 'bar'
    import {boot} from '../bar/index'
    
    console.log(boot, bear)    
    ```
0. Use webstorms `Optimize Imports` feature to merge them into one.

# Expected

The two imports should merge into one 
```ts
import {boot, bear} from 'bar
``` 

# Actual
It remains the same

```ts
import {bear} from 'bar'
import {boot} from '../bar/index'    
```

# Other related issues 
- Typing `boot` or `bear` and pressing `OPT+ENTER` doesn't import using the package name instead it is imported using a relative path.
