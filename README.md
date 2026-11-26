# bevgolf-site
bev golf website

## Shared post links

`post/index.html`, every `post/<course>/index.html` and `404.html` are
generated. Don't edit them by hand: edit `_templates/post.html`, then from a
bga-app checkout run

    node tools/link-previews/build.mjs <path to this repo>

and commit what it writes. Run it again whenever a course is added to the app,
so the course gets its page and its card as the link preview.

## Home page

`index.html` is written by hand (it isn't generated).

**Launch-update sign-ups.** Both forms post to Supabase table
`public.launch_signups` with the publishable key (bga-app migration
`supabase/migrations/20261125_launch_signups.sql`). The key can add an email
and nothing else, so read the list in the dashboard:

    select email, source, created_at from public.launch_signups order by created_at;

At launch, export it to a Resend audience and send from there. A repeat
sign-up is a 409, which the page shows as success.

**Where the pictures come from** (all in `assets/site/`):

- `holes/`: drawn from the app's `src/data/holes.ts` by bga-app
  `tools/site-art/render-holes.mjs` (usage at the top of that file). Re-render
  rather than hand-edit if a hole changes.
- `play/`: the app's Learn to Play art (`assets/Images/LearnToPlay`).
- `modes/`: the Bubble Pop game card (`assets/courseImages/CourseCard_Bubble-Pop.png`).
- `trophies.jpg`: a strip of trophy pennants on the section's background
  colour (`#06312c`), so it has no transparency to carry.
- `og.jpg`: the 1200×630 link preview for the home page.

Course logos reuse `assets/courses/`, which the link-preview build owns.
