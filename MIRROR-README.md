# OVERCLOCK arcade — deploy mirror

This repo is a DEPLOY MIRROR of `mikestays-debug/family-programs/29_games`
(the source of truth — edit there, then sync here). It exists so the arcade
can auto-deploy from Krystal's Vercel account on every push.

Sync from the family-programs clone:

    cd "family-programs" && git pull
    cd ../overclock-mirror
    rsync -a --delete --exclude .git ../family-programs/29_games/ .   # or copy manually on Windows

Then commit and push — Vercel deploys automatically.
