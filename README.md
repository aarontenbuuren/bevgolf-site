# bevgolf-site
bev golf website

## Shared post links

`post/index.html`, every `post/<course>/index.html` and `404.html` are
generated. Don't edit them by hand: edit `_templates/post.html`, then from a
bga-app checkout run

    node tools/link-previews/build.mjs <path to this repo>

and commit what it writes. Run it again whenever a course is added to the app,
so the course gets its page and its card as the link preview.
