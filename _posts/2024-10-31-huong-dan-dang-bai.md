---
layout: post
title: "Hướng dẫn sử dụng API đăng bài Devhub Blog"
date: 2024-10-31
image: "mbr-1683x1122.jpg"
author: "Ngọc Thành Đoàn" # Tên tác giả
description: "Hướng dẫn chi tiết cách sử dụng GitHub API để tạo và đăng bài viết mới vào repository Jekyll bằng script." # Mô tả ngắn cho SEO
---


# Hướng dẫn sử dụng GitHub API để tạo bài viết mới trong repository

GitHub API cho phép chúng ta tạo, cập nhật và xóa các file trực tiếp từ script hoặc các ứng dụng khác mà không cần truy cập trực tiếp vào repository. Bài viết này sẽ hướng dẫn bạn cách sử dụng API của GitHub để tạo bài viết mới vào thư mục `_posts` của repository Jekyll.

## Yêu cầu chuẩn bị

1. **GitHub Personal Access Token**: Bạn cần một token từ GitHub để xác thực cho các yêu cầu API. Token này cần được cấp quyền `repo` để có thể đọc và ghi vào repository.
2. **cURL**: Đây là công cụ dòng lệnh phổ biến để thực hiện các yêu cầu HTTP.

## Tạo GitHub Personal Access Token

1. Vào GitHub, mở **Settings** > **Developer settings** > **Personal access tokens**.
2. Chọn **Generate new token** và đặt tên cho token.
3. Cấp quyền **repo** để có thể đọc và ghi vào repository.
4. Sao chép và lưu lại token này vì bạn sẽ cần nó trong các lệnh API.

## Tạo một bài viết mới bằng GitHub API

Dưới đây là một lệnh `cURL` để tạo một bài viết mới vào thư mục `_posts` của repository.

### Cú pháp

```bash
curl -X PUT -H "Authorization: token YOUR_GITHUB_TOKEN" \
-H "Accept: application/vnd.github.v3+json" \
https://api.github.com/repos/username/your-repo/contents/_posts/2024-10-25-your-new-post.md \
-d '{
  "message": "Thêm bài viết mới",
  "committer": {
    "name": "Your Name",
    "email": "you@example.com"
  },
  "content": "'"$(echo -n '# Tiêu đề bài viết\n\nNội dung của bài viết' | base64)"'"
}'
```