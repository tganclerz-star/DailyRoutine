# Outlook Daily Routine Add-in

A personal add-in that pins a "My Routine" button to your Outlook ribbon.
Click it to open a daily checklist task pane with progress tracking.

## What's inside

```
OutlookDailyRoutine/
├── manifest.xml          # Outlook reads this to register the add-in
├── README.md             # You are here
├── assets/
│   ├── icon-16.png
│   ├── icon-32.png
│   ├── icon-64.png
│   ├── icon-80.png
│   └── icon-128.png
└── web/
    ├── taskpane.html     # The actual UI
    └── commands.html     # Required stub
```

## Step 1 - Host the files on HTTPS

The fastest free options:

### Option A: GitHub Pages (recommended)
1. Create a public GitHub repo, e.g. `outlook-daily-routine`.
2. Upload the contents of this folder (keep the `assets/` and `web/` subfolders).
3. Go to repo Settings -> Pages -> Source: `main` branch, root `/`.
4. After ~1 minute your site is live at:
   `https://<your-username>.github.io/outlook-daily-routine/`

### Option B: Azure Static Web Apps
1. Create a Static Web App in the Azure portal (free tier).
2. Connect the repo or upload via the CLI.

## Step 2 - Replace placeholders in manifest.xml

Open `manifest.xml` and replace every occurrence of:

```
https://YOUR-DOMAIN/
```

with your real HTTPS base URL, e.g.:

```
https://tomaszg.github.io/outlook-daily-routine/
```

Also generate a fresh GUID for the `<Id>` tag at https://guidgenerator.com
(optional, but recommended if you plan to share).

## Step 3 - Sideload into Outlook

### New Outlook / Outlook on the web
1. Open Outlook.
2. Ribbon -> **More apps** -> **Add apps**.
3. Click the gear icon -> **Upload custom app** -> **From file**.
4. Select `manifest.xml`.

### Classic Outlook for Windows
1. File -> **Manage Add-ins** (opens Outlook on the web).
2. **My add-ins** -> **Custom Addins** -> **Add a custom add-in** -> **Add from file**.
3. Select `manifest.xml`.

## Step 4 - Use it

1. Open any email in Outlook.
2. Look for the **Daily Routine** group on the ribbon.
3. Click **My Routine** -> the checklist opens on the right.
4. Tick tasks as you go. Progress saves per day automatically.
5. Use **Flag current email for follow-up** to category-tag the open message.

## Customising

- Edit `web/taskpane.html` to change the routine blocks, times, or tasks.
- Edit `assets/icon-*.png` to swap the icon.
- Re-upload to your host. No need to reinstall the manifest unless URLs change.

## Troubleshooting

- **Button not showing?** Make sure Reading Pane is set to Right or Bottom
  (View -> Reading Pane).
- **Blank pane?** Check the browser console (F12 in new Outlook) - usually
  an HTTPS or CORS issue from your host.
- **"Manifest invalid"?** Validate it at:
  https://github.com/OfficeDev/office-addin-validator
