# thelounge-build

Weekly build of [fHori/thelounge](https://github.com/fHori/thelounge) (`master`) with the patches in `patches/`,
published as `ghcr.io/b4remetal/thelounge`.

- Runs every Monday, on every push to `main`, and on demand (Actions → Build → Run workflow).
- Scheduled runs build without cache, so they also pick up base-image security updates.
- Tags: `latest`, `upstream-<fork commit>`, `<YYYYMMDD>`.
- A patch that no longer applies fails the build, and `latest` stays on the last good image.

## Patches

- `0001-notification-sound-off-by-default.patch`: new logins start with the notification sound off.

Add a patch: make the change in a clone of the fork, `git diff > patches/NNNN-name.patch`, commit, push.

## Running it

The image uses the official layout: data in `/var/opt/thelounge`, port 9000. Run with `--user 99:100`
(or whatever owns your data folder).
