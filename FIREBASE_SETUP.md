# Firebase Setup Guide — ShopOrder Live Sync

Follow these steps once. Takes about 10 minutes.

---

## Step 1 — Create Firebase Project

1. Go to https://console.firebase.google.com
2. Click **"Add project"**
3. Name it `shoporder` → Continue
4. Disable Google Analytics (not needed) → **Create project**

---

## Step 2 — Create Firestore Database

1. In the left sidebar click **Firestore Database**
2. Click **"Create database"**
3. Choose **"Start in test mode"** → Next
4. Select your region (e.g. `asia-south1` for India) → **Enable**

---

## Step 3 — Register Web App & Get Config

1. Click the ⚙️ gear icon → **Project settings**
2. Scroll down to **"Your apps"** → click the **`</>`** (Web) icon
3. App nickname: `ShopOrder` → click **Register app**
4. You'll see a config block like this — **copy it**:

```js
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "shoporder-xyz.firebaseapp.com",
  projectId: "shoporder-xyz",
  storageBucket: "shoporder-xyz.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abc123"
};
```

---

## Step 4 — Paste Config into index.html

Open `index.html` and find this block near the top of the `<script>`:

```js
const firebaseConfig = {
  apiKey:            "REPLACE_WITH_YOUR_API_KEY",
  authDomain:        "REPLACE_WITH_YOUR_AUTH_DOMAIN",
  projectId:         "REPLACE_WITH_YOUR_PROJECT_ID",
  storageBucket:     "REPLACE_WITH_YOUR_STORAGE_BUCKET",
  messagingSenderId: "REPLACE_WITH_YOUR_MESSAGING_SENDER_ID",
  appId:             "REPLACE_WITH_YOUR_APP_ID"
};
```

Replace the placeholder values with your actual config values.

---

## Step 5 — Set Firestore Security Rules

1. In Firebase Console → **Firestore Database** → **Rules** tab
2. Replace the content with:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /catalog/{item} {
      allow read, write: if true;
    }
    match /orders/{order} {
      allow read, write: if true;
    }
  }
}
```

3. Click **Publish**

---

## Step 6 — Import Your Stock List

1. Deploy the app (drag folder to Netlify or push to GitHub)
2. Open the app → go to **Catalog** tab
3. Drag and drop your `StkSum_xlsx_-_Stock_Summary__2_.csv` file
4. All 370 items will be uploaded to Firebase in seconds
5. Open the app on any other device — catalog appears instantly ✓

---

## Step 7 — Deploy to Netlify

1. Go to https://netlify.com → sign in
2. Click **"Add new site" → "Deploy manually"**
3. Drag the entire `shoporder/` folder onto the drop zone
4. Your live URL appears — share it with your team

Every device that opens this URL sees the same live data.

---

## How Real-Time Sync Works

| Action | What happens |
|---|---|
| Add item to catalog | Instantly appears on all devices |
| Edit item qty/unit | Updates live everywhere |
| Place order | All staff see it in Dashboard immediately |
| Mark order Delivered | Status updates live on all screens |
| Upload CSV stock list | All 370 items sync to every device |

---

## Free Tier Limits (Firebase Spark Plan)

- **50,000 reads/day** — enough for a busy shop
- **20,000 writes/day** — plenty for orders + catalog
- **1 GB storage** — more than enough
- No credit card required

If you ever need more, the Blaze (pay-as-you-go) plan costs a few rupees per month for typical usage.
