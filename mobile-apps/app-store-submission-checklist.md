# App Store Review Pre-Submission Checklist  
_For Indie Developers Shipping Simple Utility Apps (like **Yeet My Pics**)_

This checklist contains everything you should verify **before tapping “Submit for Review.”**  
Following these steps dramatically reduces rejection risk and speeds up approval.

---

## ✅ 1. Functionality & UX (Most Common Rejection Category)

- Test the **exact production build** on a real device (not simulator).
- Ensure all core actions work:
  - Photo loading  
  - Swiping to keep/delete  
  - Undo or confirmation steps (if implemented)  
  - Settings, stats, onboarding
- [x] App must handle **denied permissions** gracefully:
  - If the user denies Photos access, show a helpful message + a button linking to Settings.
- Remove any **unfinished features**, disabled buttons, placeholder screens, or lorem ipsum.
- No dead ends — every screen must offer a way back or forward.
- No crashes during:
  - First launch  
  - Permission request  
  - Swiping through many photos  
  - Returning from background  
  - Switching albums or photo access levels (if applicable)

---

## 🔐 2. Privacy & Permissions

- Ensure your **NSPhotoLibraryUsageDescription** text is clear and truthful.  
  Example:
  > “This app needs access to your photos so you can review, keep, or delete images to free up iCloud storage.”

- Only include permissions you actually use.
- Verify that your **App Privacy Nutrition Label** accurately states:
  - What data is collected  
  - Whether data is linked to the user  
  - Whether it is used for tracking  
- If collecting **no data at all**, confirm that the label says so.

---

## 📱 3. App Store Metadata

### App Name, Subtitle, Description
- Matches what the app actually does.
- No unverifiable claims (“best,” “fastest,” etc.).
- No competitor names (e.g., “Google Photos,” “iCloud Cleanup,” etc.)

### Screenshots
- Must be taken **from the actual version you are submitting**.
- No misleading UI or features that don’t exist.
- No copyrighted images unless you own the rights.

### Keywords
- Avoid trademarked product names.
- Keep them relevant to your app’s core function.

### App Preview Video (optional)
- Must show only in-app content.
- No device frames or external hardware shots.

---

## 🔗 4. Privacy Policy URL & Support URL

Your app **will be rejected instantly** if either of these fail to load.

- Privacy Policy URL:
  - Must load correctly on mobile + Safari.
  - Must match what your app actually does regarding data.
- Support URL:
  - Should show contact information and/or a help page.
  - Cannot be blank, a placeholder, or a redirect loop.

---

## 💵 5. In-App Purchases (If Applicable)

If you’re using a subscription or a lifetime unlock:

- All IAPs must be **Approved** in App Store Connect.
- Product IDs must match exactly in code.
- Test with **Sandbox accounts**:
  - Purchase flow works
  - Restore purchases works
  - UI updates correctly after purchase
- No references to IAP if you’ve removed or disabled it.

---

## 📝 6. App Review Notes (Highly Recommended)

Include a short note to the review team under **App Review Information**:

Dear App Review Team,

This app allows users to swipe through their photo library to quickly
keep or delete photos in order to free up storage space.

Key behaviors:
– Requests photo library access on first launch
– Swiping deletes or keeps photos
– No accounts, no data collection

Please let me know if you need demo info or additional clarification.
Thank you!


This greatly reduces confusion when reviewers test apps that rely heavily on system permissions.

---

## 📱 7. Device & Version Testing

Test the build on:

- At least one real iPhone (newer model preferred)
- iOS 17 and iOS 18 if available
- Different photo library sizes:
  - Empty  
  - Very large  
  - “Selected Photos Only” permission

Make sure the app responds correctly when permissions or content change.

---

## ⚙️ 8. Performance, Errors, and Edge Cases

- App should behave correctly in:
  - Low Power Mode  
  - Airplane mode (if your app does not require internet)  
  - Low battery state  
  - Limited storage situations  
- Swiping should remain responsive even with:
  - Thousands of photos  
  - Rapid swiping  
  - Switching between apps

---

## 🧹 9. Content & Compliance

- No offensive, defamatory, adult, or violent content.
- No deceptive screenshots or misleading copy.
- App icon should be:
  - Simple  
  - Original  
  - Not resembling Apple’s system icons

---

## 📦 10. Final Build Submission Checklist

Before archiving/uploading:

- Increment **Version** and **Build** numbers.
- Archive using Xcode → Product → Archive.
- Ensure no debug logs, dev UI, or test data remain.
- Verify your **App Icon** set is fully populated in all required sizes.
- Check your app’s **Settings.bundle** (if used) for accuracy.
- Re-test the archived build using TestFlight before submitting.

---

## 🎉 That’s It — You’re Ready to Ship!

Following this checklist removes the overwhelming majority of common app review issues for indie apps involving system permissions.

Good luck — and congrats on shipping! 🚀  
