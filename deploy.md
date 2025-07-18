# Ultra Kanban Deployment Guide

## Firebase Setup (Do this first!)

1. Go to [console.firebase.google.com](https://console.firebase.google.com)
2. Create project → "ultra-kanban"
3. Realtime Database → "Create Database" → "Test mode"
4. Project Settings → Your apps → Web → Register app
5. Copy the config values

## Deployment Steps

After you get your Firebase config:

1. **Update Firebase Config**
   - Replace the placeholder values in index.html lines 15-23
   - Use your actual Firebase config values

2. **Deploy to GitHub Pages**
   ```bash
   git add .
   git commit -m "Add Firebase cloud sync"
   git push origin master
   ```

3. **Enable GitHub Pages**
   - Go to GitHub.com → your repository
   - Settings → Pages
   - Source: "Deploy from branch"
   - Branch: "master" or "main"
   - Save

4. **Access Your App**
   - URL will be: `https://juanmanuelferrera.github.io/kanban/`
   - Works on any device with internet!

## Features Once Deployed

✅ Real-time sync across all devices
✅ Offline mode with automatic sync
✅ Cloud backup of all data
✅ Works on mobile, tablet, desktop
✅ Shareable URL for team collaboration

## Security Note

For production use, configure Firebase security rules:
```json
{
  "rules": {
    "users": {
      "$uid": {
        ".read": "$uid === auth.uid",
        ".write": "$uid === auth.uid"
      }
    }
  }
}
```