# 📲 App Store Review Pre-Submission Checklist  
_For indie developers shipping simple, utility-style iOS apps_

This checklist covers everything to verify **before you hit “Submit for Review.”**  
Use it to avoid the most common rejections and speed up approval.

---

## ✅ 1. Functionality & UX (Most Common Rejection Reason)

- Test the **actual production build (Archive → TestFlight)** on a real device.
- Confirm that every core action works **end-to-end**.
- Handle **denied permissions** gracefully with informative screens + a Settings deep link.
- Remove any:
  - Placeholder screens  
  - Disabled buttons  
  - Unfinished features  
  - Lorem ipsum  
- No dead ends — every screen must provide a path forward/back.
- No crashes during:
  - First launch  
  - Permission prompts  
  - Heavy content loading  
  - App resume from background  
  - Network failures (if applicable)

---

## 🔐 2. Privacy & Permissions

- All permission usage descriptions (e.g., **NSPhotoLibraryUsageDescription**) must be:
  - **Clear**
  - **Accurate**
  - **Non-generic**
- Only request permissions you truly use.
- Double-check your **Privacy Nutrition Label**:
  - Data collected  
  - Linked to user?  
  - Used for tracking?  
- If you collect nothing, ensure the label reflects **no data collection**.

---

## 🛍️ 3. App Store Metadata

### App Name, Subtitle, Description
- Reflect what the app actually does.  
- Avoid unverifiable claims (“best,” “#1,” “fastest”).  
- No competitor or trademark names.

### Screenshots
- Must match the **exact build** you’re submitting.
- No mockups of features you haven’t implemented.
- No copyrighted or unlicensed imagery.

### Keywords
- Only include relevant, non-trademarked terms.

### App Preview Video (optional)
- Only show in-app behavior.  
- No device frames or external footage.

---

## 🔗 4. Required URLs (Privacy Policy & Support)

A broken URL = **automatic rejection**.

- **Privacy Policy URL**
  - Must load quickly on Safari.
  - Content must describe your actual data practices.
- **Support URL**
  - Provide real help/contact info (FAQ, email, etc.).
  - No placeholders or empty pages.

---

## 💵 5. In-App Purchases (If Your App Includes Them)

- All products must show **“Approved”** in App Store Connect.
- Product IDs must match exactly in your code (case-sensitive).
- Test using **TestFlight + Sandbox accounts**:
  - Purchase flow  
  - Restore purchases  
  - UI state after purchase  
- Remove any UI references to IAP you’re not using.

---

## 📝 6. App Review Notes (Optional but Highly Recommended)

Use **App Review Information → Notes** to explain your app clearly.

Dear App Review Team,

This app provides a simple utility for users to __________.

Key Behaviors:
– Requests ______ permission on first launch
– Core actions: __________
– No data collection / or specify what you collect

Let me know if you need demo info, credentials, or clarification.
Thank you!


This prevents confusion for apps relying on permissions, gestures, or non-obvious flows.

---

## 📱 7. Device, OS, and Scenario Testing

Test across:

- At least one real iPhone (ideally a recent model)
- Latest iOS version (and one prior, if available)
- Different user states:
  - No content  
  - Lots of content  
  - Restricted permissions  
  - Airplane mode  
  - Slow/unstable network (if applicable)

---

## ⚙️ 8. Performance, Responsiveness & Edge Cases

- Test in:
  - Low Power Mode  
  - Low storage  
  - Low battery  
  - App switching  
- UI should remain responsive during:
  - Rapid actions  
  - High-volume interactions  
  - Large data sets  
- No debug logs, console spam, or temporary UI.

---

## 🧹 9. Content & Compliance

- No offensive, sexual, discriminatory, or violent content.
- No misleading screenshots or exaggerated claims.
- App icon must be:
  - Original  
  - Simple  
  - Not mimicking Apple icons

---

## 📦 10. Build & Submission Prep

Before uploading:

- Increment **Version** and **Build** numbers.
- Archive via Xcode → Product → Archive.
- Confirm:
  - Correct bundle ID  
  - Proper signing & provisioning  
  - App Icon set is complete  
  - No debug/test data stored  
- Install & test the **archived build** via TestFlight before submitting.
- Ensure your App Store Connect entry is 100% filled out:
  - Description  
  - Screenshots  
  - Keywords  
  - URLs  
  - IAP entries (if any)

---

## 🚀 You’re Ready to Ship!

This checklist covers the most common rejection points for indie, utility, and simple content-based apps.  
If everything checks out, hit **Submit for Review** with confidence.

Congrats on shipping your app! 🎉
