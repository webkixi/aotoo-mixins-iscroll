# aotoo-mixins-iscroll
mixin iscroll, Integrated the iscroll library to aotoo

## Dependencies


## Install
```
// install
npm install aotoo-common
npm install aotoo-mixins-iscroll --save
```

## Usage 
```js
require('aotoo-mixins-scroll')

// inject css into head
Aotoo.inject.css( `
  .iscrollBox{
    height: 400px;
    overflow: hidden;
  }
`)

/*
 I. listTest.render() is a jsx  
 
 II. listTest.render(id) will mount jsx into the dom about that id, like React.render(...)  
 
 III. listTest.render(id, callback)  callback will be executed after jsx be mounted into the dom about that id  
*/
const listData = {
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

const IscrollList = Aotoo.iscroll((
  <div className='iscrollBox'>
    <Aotoo.list data={listData}/>
  </div>
), {
  elements: '.img',
  onscroll: function(lazy, direction){
    console.log('====== 1111');
  },
  onscrollend: function(lazy) {
    console.log('====== 2222');
  }
})

Aotoo.render(<IscrollList />, 'test')
```

