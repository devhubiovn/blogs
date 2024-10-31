# blogs
sudo gem install bundler jekyll
bundle install
bundle exec jekyll serve --host 0.0.0.0

```
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

cp $(bundle show minima)/_layouts/default.html _layouts/
cp $(bundle show minima)/_layouts/post.html _layouts/
