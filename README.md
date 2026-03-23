### Observation Checkpoint 1 — Level 1
**Command:** `df -h | grep loop`

**Screenshot:**
![Level 1 screenshot](screenshots/level1.png)

**Explanation:**
The output shows `/dev/loop50` and `/dev/loop51` are successfully mounted at
`/media/g11-thoeun-yanit/880a613e-ec20-4e3f-a877-23c6081b8e3b` and `/media/g11-thoeun-yanit/bbef61db-b8e8-44d7-a870-a6bc52a20b59`
respectively. This proves both virtual disk images have been attached to loopback
devices and recognized by the kernel as mounted file systems without root privileges.

---

## Observation Checkpoint 2 — Level 3
**Command:** `ps aux | grep sync_`

**Screenshot 1 — ps aux Output:**
![Level 3 screenshot](screenshots/level3.png)

**Explanation:**
`sync_up` held the Alpha lock and was waiting for Beta. `sync_down` held the Beta
lock and was waiting for Alpha. Neither script could proceed because each was
blocked by the other — a classic circular wait. Both processes hung indefinitely
and never reached `"Sync complete."`

---

## Observation Checkpoint 3 — Level 4
**Screenshot — Frozen Terminal:**
![Level 4 screenshot](screenshots/level4.png)

**Explanation:**
Both players were completely frozen simultaneously across two separate user accounts.
This simulates a distributed denial of service because the entire DR sync system
was rendered non-functional across multiple users — not just a single process —
requiring manual intervention to recover.