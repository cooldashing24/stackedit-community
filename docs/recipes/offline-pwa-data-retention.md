# Offline PWA Architecture & Local Data Retention in StackEdit++

> **Platform**: [StackEdit++](https://stackeditplusplus.meshworld.in) • [Live App](https://stackeditplusplus.meshworld.in/app)  
> **Storage Target**: Browser IndexedDB & Cache Storage API

---

## Overview

StackEdit++ is designed to function as an offline-first Progressive Web Application (PWA). Once loaded in your browser, the service worker caches all static application assets—JavaScript runtime bundles, stylesheets, typography, and offline fonts. Your markdown documents and workspace settings are written directly to the browser's sandboxed **IndexedDB** database.

---

## 1. Storage Layers in StackEdit++

```
┌────────────────────────────────────────────────────────┐
│                   BROWSER CLIENT SANDBOX               │
│                                                        │
│   ┌────────────────────────┐  ┌────────────────────┐   │
│   │     Service Worker     │  │     IndexedDB      │   │
│   │   (CacheStorage API)   │  │   (Local DB Store) │   │
│   │                        │  │                    │   │
│   │ • Core App JS Bundles  │  │ • Markdown Files   │   │
│   │ • CSS & Web Fonts      │  │ • File Metadata    │   │
│   │ • KaTeX / Math Assets  │  │ • History & Diffs  │   │
│   │ • Mermaid Engine       │  │ • User Settings    │   │
│   └────────────────────────┘  └────────────────────┘   │
└────────────────────────────────────────────────────────┘
```

---

## 2. Ensuring Persistent Storage

Modern browsers (Chrome, Edge, Firefox, Safari) apply storage eviction algorithms when disk space is constrained, prioritizing "best-effort" storage. You can grant StackEdit++ **Persistent Storage** permission so the browser will never evict your local notes without explicit user confirmation.

### Checking Storage Persistence Status
In browser DevTools (Console):

```javascript
// Check whether storage is marked as persistent
if (navigator.storage && navigator.storage.persisted) {
  navigator.storage.persisted().then(persistent => {
    console.log(`Storage persistent: ${persistent}`);
  });
}
```

### Requesting Persistent Storage
```javascript
// Request browser to protect your database from automatic eviction
if (navigator.storage && navigator.storage.persist) {
  navigator.storage.persist().then(granted => {
    if (granted) {
      console.log("Persistent storage granted. Documents are safe from eviction.");
    }
  });
}
```

### Estimating Available Quota
```javascript
if (navigator.storage && navigator.storage.estimate) {
  navigator.storage.estimate().then(({ usage, quota }) => {
    const usageMB = (usage / (1024 * 1024)).toFixed(2);
    const quotaMB = (quota / (1024 * 1024)).toFixed(2);
    console.log(`Using ${usageMB} MB of ${quotaMB} MB quota.`);
  });
}
```

---

## 3. Data Safety Checklist

| Action / Event | Notes Persist? | Explanation |
| :--- | :--- | :--- |
| **Close Tab / Close Browser** | ✅ Yes | Documents are written immediately to IndexedDB. |
| **Device Reboot / OS Restart** | ✅ Yes | Persistent database on local disk storage. |
| **No Internet / Offline Mode** | ✅ Yes | Service worker serves the cached application shell. |
| **PWA Installed to Desktop/Mobile** | ✅ Yes | Runs in an isolated standalone window with persistent storage. |
| **Clear Cookies and Site Data** | ❌ No | Manually clearing browser site data deletes IndexedDB. |
| **Incognito / Private Browsing** | ⚠️ Ephemeral | Notes are deleted as soon as the private window is closed. |

---

## 4. Disaster Recovery & Manual Backups

Because StackEdit++ does not maintain a copy of your files on a remote server, we recommend periodic local backups:
1. **Export Single Note**: Use the export menu to download `.md` files directly to your local file system.
2. **Export Workspace**: Export your workspace archive or backup settings periodically.
3. **Version Control**: For critical documentation, save exported Markdown files into a local Git repository.
