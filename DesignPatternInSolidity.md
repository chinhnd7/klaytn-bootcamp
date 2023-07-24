# Design Pattern in Solidity

## SECURITY PATTERN
### Checks-Effects-Interactions pattern
Kiểm tra - Thay đổi - Tương tác, quy trình đảm bảo kiểm tra điều kiện an toàn

```solidity
function auctionEnd() public {
    // check require(now >= auctionEnd)
    require(!ended);

    // Effects
    ended = true;

    // Interaction
    beneficiary.transfer(highestBid);
}
```

## FACTORY PATTERN
- Ý tưởng của factory pattern:
Có 1 hợp đồng (factory) sẽ thực hiện việc tạo ra các hợp đồng khác.
Factory pattern sinh ra để tổ chức code theo nguyên lý S trong Solid: Single Responsibility Principle
- Một class không cần biết cách tạo các instance của các class khác, và pattern này cung cấp sự trừu tượng cho hàm tạo.

### Normal Factory Pattern
- Tạo contract Factory có chức năng xử lý việc tạo hợp đồng con và có thể thêm các chức năng khác để quản lý hiệu quả các contract này (ví dụ: tìm kiếm một hợp đồng cụ thể hoặc vô hiệu hóa contract)

## Proxy Contract
- Hợp đồng chuyển tiếp tất cả các cuộc gọi đến một hợp đồng khác, gọi là hợp đồng triển khai
- Sử dụng:
    + Thêm Logic
    + Nâng cấp ảo (các hợp đồng hiện tại vẫn không thể thay đổi): một phiên bản mới có thể được triển khai và địa chỉ của nó thay thế phiên bản cũ trong bộ nhớ
    + Tránh phá vỡ sự phụ thuộc của các hợp đồng khác đang tham chiếu hợp đồng được nâng cấp
