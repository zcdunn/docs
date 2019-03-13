---
title: Updating your instance
icon: arrow-up
summary: 'Plume is still unstable and regularly gets new features and bug fixes. Keeping your
instance up-to-date is important.'
---

To update your instance, run these commands with `plume` user if you created it, or with your default user, in the Plume directory.

```bash
git pull origin master
cargo web deploy -p plume-front
# Rebuild the backend and CLI
# Replace DATABASE with either postgres or sqlite, depending on the choice you made on installation
cargo install --force && cargo install --no-default-features --features DATABASE --path plume-cli --force

# Run the migrations
diesel migration run

# If you are using sysvinit
sudo service plume restart

# If you are using systemd
sudo systemctl restart plume
```

That's it!
