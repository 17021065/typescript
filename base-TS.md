# TYPESCRIPT CƠ BẢN

## Định nghĩa
TypeScript là một ngôn ngữ bổ trợ cho JavaScript, nó cung cấp cho JS một layer kiểm tra các hoạt động bất thường xảy ra trong hệ thống, giúp lập trình viên có thể hạn chế những lỗi vô hình được tạo ra bởi quy tắc lỏng lẻo của JS. TS không làm thay đổi cơ chế, cú pháp, hay hành vi runtime của JS, TS chỉ đơn thuần là phát hiện và cảnh báo các lỗi có thể xảy ra, những đoạn code viết bằng JS vẫn có thể chạy bình thường trong TS.

## Mục đích sử dụng
JS cung cấp một số kiểu dữ liệu nguyên thủy như là `string` hay `number`, nhưng lại không hề kiểm tra những dữ liệu được gán có đúng kiểu dữ liệu của biến hay không.

Ví dụ: 
```js
  let number = 1;
  number = 'one';
  console.log(number); // one
```
Biến `number` được khởi tạo với kiểu dữ liệu `Number` nhưng sau đó lại có thể tự do gán cho nó một giá trị thuộc kiểu dữ liệu `String`. Các kiểu dữ liệu khác nhau có quy tắc xử lí khác nhau, việc có thể tự do thay đổi kiểu dữ liệu của biến có thể gây ra rất nhiều lỗi tiềm ẩn.
Với việc sử dụng TS, compiler hoặc editer có thể đưa ra những cảnh báo về việc gán sai kiểu dữ liệu, giúp phòng tránh những vấn đề như trên xảy ra.

## Cú pháp
TS định nghĩa kiểu dữ liệu cho biến bằng cú pháp `name: type`. Ví dụ:
```js
  let price: number;
  let name: string;
```
TS cũng có thể định nghĩa kiểu dữ liệu cho đối số và giá trị trả về của hàm.
```js
  class Product = {
    name: string;
    price: number;
  }
  const findProduct = (name: string) :Product => {
    //...
  }
```

## Kiểu kết hợp 
Trong TS, ta có thể tạo ra một kiểu dữ liệu phức tạp bằng cách kết hợp các kiểu dữ liệu đơn giản. Có 2 cách để làm điều này đó là **Union** và **Genetic**

### Union
Với Union, ta có thể tạo một kiểu dữ liệu gồm nhiều kiểu khác nhau. Ví dụ:
```js
// Variable
  type WindowStates = "open" | "closed" | "minimized";
  type LockStates = "locked" | "unlocked";
  type PositiveOddNumbersUnderTen = 1 | 3 | 5 | 7 | 9;

// Function 
  const  getLength = (obj: string | string[]) => {
    return obj.length;
  }
```

### Genetic
Với Genetic ta cũng cấp biến kiểu dữ liệu cho các kiểu dữ liệu không nguyên thủy, điển hình là `Array`
```js
  type StringArray = Array<string>;
  type NumberArray = Array<number>;
  type ObjectWithNameArray = Array<{ name: string }>;
```

### Structural Type System
Cơ chế kiểm tra kiểu dữ liệu của TS tập trung vào hình dạng của giá trị. Nếu 2 object có cùng cấu trúc, chúng được coi là có cùng kiểu dữ liệu dù chúng không được khai báo giống nhau.
Ví dụ:
```js
  interface Point {
    x: number;
    y: number;
  }
  
  function logPoint(p: Point) {
    console.log(`${p.x}, ${p.y}`);
  }
  
  // logs "12, 26"
  const point = { x: 12, y: 26 };
  logPoint(point);
```
Biến `point` mặc dù không được khai báo với kiểu `Point` nhưng nó có cùng cấu trúc nên TS sẽ nhận định kiểu dữ liệu của nó là `Point`.