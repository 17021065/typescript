# MỘT SỐ QUY TẮC TRONG TYPESCRIPT

## Không dùng `any`
`any` là kiểu dữ liệu đặc biệt, ta có thể gán bất cứ giá trị nào cho nó, điều này khiến ta không thể nhận được sự đảm bảo về kiểu dữ liệu của TS. 
Ta có thể bật bộ kiểm tra `any` bằng option **noImplicitAny** trong file cấu hình.

## Kiểm tra kĩ lưỡng `null` và `undefined`
Tất cả các kiểu dữ liệu đều có thể có 2 giá trị `null` và `undefined`, mà 2 giá trị này thường xuyên gây ra lỗi trong JS, vậy nên việc kiểm tra kĩ các trường hợp này là rất quan trọng.
Ta có thể bật bộ kiểm tra `null` và `undefined`bằng option **strictNullChecks** trong file cấu hình.

## Không dùng `this` với kiểu dữ liệu `any`
`this` được gán kiểu dữ liệu mặc định là `any`, vì vậy nếu không gán một kiểu dữ liệu rõ ràng cho `this` nó có thể gây ra các vấn đề tương tự như khi sử dụng `any`
Ta có thể bật bộ kiểm tra kiểu dữ liệu cho `this` bằng option **noImplicitThis** trong file cấu hình.