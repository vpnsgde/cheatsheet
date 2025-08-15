# HTML Mastery Cheat Sheet

## 1. Cấu trúc cơ bản của HTML5

``` html
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tiêu đề trang</title>
</head>
<body>
    Nội dung trang web...
</body>
</html>
```

## 2. Thẻ cơ bản

| Thẻ             | Mô tả                              |
| --------------- | ---------------------------------- |
| `<h1>` → `<h6>` | Tiêu đề (h1 lớn nhất, h6 nhỏ nhất) |
| `<p>`           | Đoạn văn                           |
| `<br>`          | Xuống dòng                         |
| `<hr>`          | Gạch ngang                         |
| `<span>`        | Nội dung inline                    |
| `<div>`         | Khối nội dung (block)              |


## 3. Liên kết & Ảnh

``` html
<a href="https://example.com" target="_blank">Đi tới Example</a>
<img src="image.jpg" alt="Mô tả ảnh" width="200" height="150">
```

## 4. Danh sách

``` html
<!-- Danh sách không thứ tự -->
<ul>
    <li>Mục 1</li>
    <li>Mục 2</li>
</ul>

<!-- Danh sách có thứ tự -->
<ol>
    <li>Bước 1</li>
    <li>Bước 2</li>
</ol>

<!-- Danh sách mô tả -->
<dl>
    <dt>HTML</dt>
    <dd>Ngôn ngữ đánh dấu siêu văn bản</dd>
</dl>
```

## 5. Bảng

``` html
<table border="1">
    <thead>
        <tr>
            <th>Tên</th>
            <th>Tuổi</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Lan</td>
            <td>25</td>
        </tr>
    </tbody>
</table>
```

## 6. Form

``` html
<form action="/submit" method="POST">
    <label for="name">Họ tên:</label>
    <input type="text" id="name" name="name" required>

    <label>Mật khẩu:</label>
    <input type="password" name="pass">

    <input type="submit" value="Gửi">
</form>
```

## 7. Media

``` html
<video controls width="400">
    <source src="video.mp4" type="video/mp4">
    Trình duyệt không hỗ trợ video.
</video>

<audio controls>
    <source src="audio.mp3" type="audio/mpeg">
    Trình duyệt không hỗ trợ audio.
</audio>
```

## 8. Semantic HTML5

  Thẻ           Ý nghĩa
  ------------- ------------------
  `<header>`    Phần đầu trang
  `<nav>`       Thanh điều hướng
  `<main>`      Nội dung chính
  `<section>`   Phần nội dung
  `<article>`   Bài viết độc lập
  `<aside>`     Nội dung phụ
  `<footer>`    Chân trang

## 9. Meta & SEO

``` html
<meta name="description" content="Mô tả trang cho SEO">
<meta name="keywords" content="html, css, javascript">
<meta name="author" content="Tên tác giả">
```

## 10. Thuộc tính toàn cục

  Thuộc tính   Mô tả
  ------------ --------------------
  `id`         Định danh duy nhất
  `class`      Phân loại nhóm CSS
  `style`      CSS inline
  `title`      Tooltip khi hover
  `hidden`     Ẩn phần tử
  `tabindex`   Thứ tự tab focus

## 11. HTML nâng cao

``` html
<!-- Iframe -->
<iframe src="https://example.com" width="600" height="400"></iframe>

<!-- Data Attributes -->
<div data-user-id="123" data-role="admin"></div>

<!-- Canvas -->
<canvas id="myCanvas" width="200" height="100"></canvas>
```

## 12. Mẹo & Best Practices

-   Dùng **HTML semantic** để cải thiện SEO & accessibility.\
-   Luôn thêm `alt` cho ảnh.\
-   Dùng **`<label>`** liên kết với input để cải thiện UX.\
-   Xác thực HTML bằng [W3C Validator](https://validator.w3.org/).\
-   Giữ cấu trúc HTML sạch, tách riêng CSS & JS.
