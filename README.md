# CampusKit Management Centre

A separate admin website for the CampusKit student platform.

## Features
- Payment request review (pending, approved, rejected) through the existing CampusKit payments API. Accept activates the matching entitlement; Reject leaves access locked.
- Supports AI Premium (₹59), Intelligence Lab tools (₹5–₹30), and 37 Class XII practical projects (₹20/₹40).
- Firebase Auth user listing and enable/disable account controls.
- Public music playlist management using the existing Firestore `publicMusic` collection.
- Responsive dark blue management dashboard.

## Deployment
This repository includes a GitHub Pages Actions workflow. In GitHub, open **Settings → Pages** and set **Build and deployment → Source: GitHub Actions** if it is not already selected.

After deployment, add the published Pages hostname to Firebase Authentication → Settings → Authorized domains.

## Required Vercel environment variable
In the existing `campuskit` Vercel project, set:
- `CAMPUSKIT_ADMIN_EMAILS`: comma-separated authorized admin emails. The current production value is already configured for the three approved admin accounts.

The existing `FIREBASE_SERVICE_ACCOUNT` variable is used by the API and must remain private. Never put service-account JSON in this repository or frontend.

## API
The admin UI calls the existing API at `https://campuskit-six.vercel.app/api/payments`. The API verifies Firebase ID tokens and checks the admin email server-side before exposing admin operations.
