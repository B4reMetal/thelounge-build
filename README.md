# thelounge-build

Build of [fHori/thelounge](https://github.com/fHori/thelounge) (`master`) with the patches in `patches/`,
published as `ghcr.io/b4remetal/thelounge`.

- Checks fHori's `master` every 30 minutes and builds when it has a commit with no image yet.
- Also runs every Monday, on every push to `main`, and on demand (Actions → Build → Run workflow).
- The Monday run builds without cache, so it also picks up base-image security updates.
- Tags: `latest`, `upstream-<fork commit>`, `<YYYYMMDD>`.
- A patch that no longer applies is skipped with a warning on the run, and the image is built without it.

## Patches

- `0001-notification-sound-off-by-default.patch`: new logins start with the notification sound off.

Add a patch: make the change in a clone of the fork, `git diff > patches/NNNN-name.patch`, commit, push.

## Running it

The image uses the official layout: data in `/var/opt/thelounge`, port 9000. Run with `--user 99:100`
(or whatever owns your data folder).
