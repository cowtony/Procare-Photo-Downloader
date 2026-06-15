# ProCare Photo & Video Downloader (Mac)

Bulk-download all your child's photos and videos from ProCare, organized by month, with the correct date set on every file.

## 1. Get your token

1. Log in to ProCare in Chrome → open the **Photos** tab.
2. Press `F12` → click **Network** → refresh the page.
3. Click any request named `photos?page=...`.
4. In **Request Headers**, find:
   `authorization: Bearer online_auth_xxxxxxxx`
5. Copy the part after `Bearer `.

Open `fetch_procare.sh` in any text editor and paste it into the `TOKEN=` line near the top:

```bash
TOKEN="online_auth_PASTE_YOURS_HERE"
```

> Token expires after a while. If the script fails with 401/403, repeat this step.
> Don't share your token — it's tied to your account.

## 2. Run it

Open Terminal, `cd` to the folder with the script, then:

```bash
# one month
bash fetch_procare.sh 2024-11

# a range (inclusive)
bash fetch_procare.sh 2024-08 2025-06
```

You'll get folders like:

```
2024-08/
  ├── photos/
  └── videos/
```

Drag them into Apple Photos / Google Photos — dates will be correct.

Re-running is safe: existing files are skipped.
