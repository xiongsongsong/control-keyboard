##构想

这是一个构思中的项目，主要想法是在网页中自行一些自动化的操作。

##为了节约时间，基于jQuery

```javascript
var control = require('control-keyboard')

//press A
control.press('A')

//隔120ms输入A..B..C,然后按Ctrl+A，再按Ctrl+C，然后获取#abc
control.press('ABC',120)
.combo('ctrl+A')
.combo('ctrl+C')
.get('#abc')
.focus()
.combo('ctrl+V')
.then(function(next){
    var i = 0
    var self=this
    var cl= setInterval(function(ev){
        if(i++>5){
            clearInterval(cl)
            self.get('#def').focus()
            next()
        }
    },1000)
})
.press(32)
.get('#send')
.trigger('click')
//press A
```