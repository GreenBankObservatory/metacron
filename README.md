# metacron
Check crontabs across multiple users/hosts via SSH


1. Reads `METACRON_USERHOSTS` env variable (format `user@host user@host ...`)
2. SSH's to each user/host and prints the crontab

## Example Usage

```bash
$ export METACRON_USERHOSTS="userA@hostA userA@hostB userB@hostC"
$ metacron | grep nameOfScript
--- Checking cron for: userA@hostA ---
--- Checking cron for: userA@hostB ---
00 8 * * * /bin/nameOfScript
--- Checking cron for: userB@hostC ---
```

Here we see that `nameOfScript` was found in the crontab for `userA@hostB`

You will probably want to instead define `METACRON_USERHOSTS` in your `.bashrc`
