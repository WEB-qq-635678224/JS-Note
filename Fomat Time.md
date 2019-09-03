```js
 format: function( times ){
            Date.prototype.Format = function(fmt)   
                { 
                var o = {   
                    "M+" : this.getMonth()+1,                 //月份   
                    "d+" : this.getDate(),                    //日   
                    "h+" : this.getHours(),                   //小时   
                    "m+" : this.getMinutes(),                 //分   
                    "s+" : this.getSeconds(),                 //秒   
                    "q+" : Math.floor((this.getMonth()+3)/3), //季度   
                    "S"  : this.getMilliseconds()             //毫秒   
                };   
                if(/(y+)/.test(fmt))   
                    fmt=fmt.replace(RegExp.$1, (this.getFullYear()+"").substr(4 - RegExp.$1.length));   
                for(var k in o)   
                    if(new RegExp("("+ k +")").test(fmt))   
                fmt = fmt.replace(RegExp.$1, (RegExp.$1.length==1) ? (o[k]) : (("00"+ o[k]).substr((""+ o[k]).length)));   
                return fmt;   
            }  

           return times.format("yyyy-MM-dd");  

  },
  
  
  formatDate: function( times ){ 
                let date = new Date( times),
                    Y = date.getFullYear() + '-',
                    M = (date.getMonth()+1 < 10 ? '0'+(date.getMonth()+1) : date.getMonth()+1) + '-',
                    D = date.getDate() < 10 ? '0'+ date.getDate() + ' ' : date.getDate() + ' ' ,
                    H = date.getHours() < 10 ? '0' + date.getHours() + ':' : date.getHours() + ':' ,
                    MS = date.getMinutes() <10 ? '0' + date.getMinutes() + ':' :date.getMinutes() + ':',
                    S = date.getSeconds() < 10 ? '0' + date.getSeconds() : date.getSeconds(); 
                return Y+M+D+H+MS+S 
        },
```
 
