# aotoo-mixins-scroll
mixin scroll, about Listen to the scroll event and lazyload something"

## Dependencies

Pls install `aotoo` first, and make `aotoo` as a global variable with the variable name `Aotoo`
```js
npm install aotoo  or
yarn add aotoo

// ------------ some js file

import aotoo from aotoo
window.Aotoo = aotoo
...
```

## Install
```
// install
npm install aotoo-mixins-iscroll --save
```

## Usage 
```js
require('aotoo-mixins-scroll')

// Aotoo inject library
// Refer to https://github.com/webkixi/aotoo-inject
const inject = Aotoo.inject()

// it is a plugin of aotoo
import treex from 'aotoo-react-treex'

/*
 I. treeTest.render() is a jsx  
 
 II. treeTest.render(id) will mount jsx into the dom about that id, like React.render(...)  
 
 III. treeTest.render(id, callback)  callback will be executed after jsx be mounted into the dom about that id  
*/
const treeTest = treex({
  props: { 
    data: [
      {title: '1111'},
      {title: '2222'},
      {title: '1111'},
      {title: '2222'},
      {title: '1111'},
      {title: '2222'},
      {title: '1111'},
      {title: '2222'},
      {title: '1111'},
      {title: '2222'},
      {title: '1111'},
      {title: '2222'},
      {title: <div className="img">abcdefg</div>},
      {title: '2222'},
      {title: '1111'},
      {title: '2222'},
      {title: '3333'} 
    ]
  }
})

function IscrollBox(props){
  return <div className='iscrollBox'>{treeTest.render()}</div>
}

const IscrollList = Aotoo.iscroll(<IscrollBox />, {
  elements: '.img',
  onscroll: function(lazy, direction){
    console.log('====== 1111');
  },
  onscrollend: function(lazy) {
    console.log('====== 2222');
  }
})

// inject css into head
inject.css(
`
 .iscrollBox{
    height: 400px;
    overflow: hidden;
  }
`
, function(){
  // mount jsx into dom that id is test
  Aotoo.render(<IscrollList />, 'test')
})

```

