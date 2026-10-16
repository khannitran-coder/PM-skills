# Gherkin Patterns — Complex Cases

Read this when a story involves multiple states, roles/permissions, or
multi-step flows that a simple Given/When/Then doesn't capture cleanly.

## Multiple Preconditions (And)

```
Scenario: Duyệt đơn hàng vượt hạn mức
Given tôi đăng nhập với vai trò "Trưởng phòng"
And đơn hàng có giá trị vượt hạn mức duyệt của "Nhân viên"
When tôi bấm "Duyệt"
Then hệ thống ghi nhận duyệt thành công và gửi email xác nhận cho người tạo đơn
```

## Role/Permission Variants — write one scenario per role, don't merge

Don't write "Given tôi đăng nhập (bất kỳ vai trò nào)" — that hides a
permission bug waiting to happen. Split explicitly:

```
Scenario: Nhân viên xem đơn hàng của mình
Given tôi đăng nhập với vai trò "Nhân viên"
When tôi vào danh sách đơn hàng
Then tôi chỉ thấy đơn hàng do tôi tạo

Scenario: Trưởng phòng xem đơn hàng của cả phòng
Given tôi đăng nhập với vai trò "Trưởng phòng"
When tôi vào danh sách đơn hàng
Then tôi thấy tất cả đơn hàng của phòng mình

Scenario: Nhân viên cố truy cập đơn hàng không thuộc quyền
Given tôi đăng nhập với vai trò "Nhân viên"
When tôi truy cập trực tiếp URL đơn hàng của người khác
Then hệ thống chặn và trả về lỗi "Không có quyền truy cập"
```

## Multi-Step Flow — use Scenario Outline for data variations

When the same flow repeats with different data, don't write N nearly
identical scenarios — use a table:

```
Scenario Outline: Validate email format khi đăng ký
Given tôi ở màn hình đăng ký
When tôi nhập email "<email>"
Then hệ thống hiển thị "<result>"

Examples:
| email              | result                    |
| a@b.com            | Email hợp lệ              |
| a@@b.com           | Lỗi định dạng email       |
| (để trống)         | Lỗi bắt buộc nhập         |
```

## Background — shared Given across scenarios in one story

If every scenario in a story shares the same setup, factor it out instead
of repeating it:

```
Background:
Given tôi đăng nhập với vai trò "Kế toán viên"
And có ít nhất 1 hóa đơn ở trạng thái "Chưa thanh toán"

Scenario: ...
Scenario: ...
```

## Common Mistake to Flag

A Then step that describes an internal implementation detail instead of an
observable outcome ("Then hệ thống gọi API xử lý thanh toán") isn't
testable from a user/business perspective — rewrite as the outcome the
user or business would actually observe ("Then trạng thái đơn hàng
chuyển thành 'Đã thanh toán' và khách hàng nhận email xác nhận").
