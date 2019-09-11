# 接口 `interface`

> 定义接口使用  `interface`  关键字

```typescript
// 定义接口 
interface SquareConfig {
    color?: string; // ? 表示非必填

    width?: number;
}

// 使用 void代表没有返回值
function createSquare(config:SquareConfig):void{
    // ...
}

// 这里会报错
let mySquare = createSquare({ colour: "red", width: 100 }); 
// error: 'colour' not expected in type 'SquareConfig' 
// 因为 单词拼写错误 'colour' !== 'color'
let mySquare = createSquare({ color: "red", width: 100 }); // ok


// 索引签名
interface SquareConfig {
    color?: string;
    width?: number;
    [propName: string]: any;
}

let mySquare = createSquare({ colour: "red", width: 100 }); // ok
```


