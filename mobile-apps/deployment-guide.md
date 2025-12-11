# TestFlight Deployment Guide

Complete guide for deploying "Yeet My Pics" to Apple TestFlight, including initial launch and subsequent updates.

## Prerequisites

- ✅ Paid Apple Developer account (active)
- ✅ Logged into Apple Developer account
- ✅ TestFlight app installed on test device
- ✅ Xcode installed on Mac
- ✅ Flutter SDK installed and configured

## App Information

- **App Name**: Yeet My Pics
- **Bundle Identifier**: `com.yeetmypics.yeetMyPics`
- **Current Version**: `1.0.0+1` (version+build)
- **Platform**: iOS

---

## Part 1: Initial TestFlight Launch

### Step 1: Verify Bundle Identifier

Your bundle ID is `com.yeetmypics.yeetMyPics`. This must match what you register in App Store Connect.

**Location**: `ios/Runner.xcodeproj/project.pbxproj`
- Search for `PRODUCT_BUNDLE_IDENTIFIER` to verify

### Step 2: Configure Xcode Signing

1. **Open the workspace** (not the project file):
   ```bash
   open ios/Runner.xcworkspace
   ```
   ⚠️ **Important**: Use `.xcworkspace`, not `.xcodeproj`

2. **In Xcode**:
   - Select the **Runner** project in the left sidebar
   - Select the **Runner** target (under TARGETS)
   - Navigate to **Signing & Capabilities** tab
   - Check **"Automatically manage signing"**
   - Select your **Team** (your Apple Developer account)
   - Xcode will automatically create provisioning profiles

3. **Verify Bundle Identifier** matches `com.yeetmypics.yeetMyPics`

### Step 3: Create App in App Store Connect

1. Go to [appstoreconnect.apple.com](https://appstoreconnect.apple.com)
2. Click **"My Apps"** → **"+"** → **"New App"**
3. Fill in the required information:
   - **Platform**: iOS
   - **Name**: Yeet My Pics
   - **Primary Language**: English (or your preference)
   - **Bundle ID**: Select `com.yeetmypics.yeetMyPics` from dropdown
     - If it doesn't exist, click **"Register a new Bundle ID"** first
   - **SKU**: Unique identifier (e.g., `yeet-my-pics-001`)
   - **User Access**: Full Access (or Limited if you have a team)
4. Click **"Create"**

### Step 4: Build App for Release

**Option A: Using Flutter CLI (Recommended)**

```bash
# Navigate to project root
cd /Users/petemcpherson/Coding\ Projects/yeet_my_pics

# Clean previous builds (optional but recommended)
flutter clean

# Build iOS release archive
flutter build ipa
```

This creates an `.ipa` file at: `build/ios/ipa/yeet_my_pics.ipa`

**Option B: Using Xcode**

1. In Xcode, select **Product** → **Archive**
2. Wait for archive to complete (may take a few minutes)
3. The Organizer window should open automatically

### Step 5: Upload to App Store Connect

**Option A: Using Xcode Organizer (Recommended)**

1. After archiving, the **Organizer** window opens automatically
2. Select your archive
3. Click **"Distribute App"**
4. Choose **"App Store Connect"**
5. Click **"Next"**
6. Choose **"Upload"** (not Export)
7. Select your team and signing options (usually automatic)
8. Review app information
9. Click **"Upload"**
10. Wait for upload to complete (5-15 minutes)
11. You'll see a success message when done

**Option B: Using Transporter App**

1. Download **Transporter** from Mac App Store (if needed)
2. Open Transporter app
3. Drag your `.ipa` file from `build/ios/ipa/` into Transporter
4. Click **"Deliver"**
5. Wait for upload to complete

### Step 6: Process Build in App Store Connect

1. Go to [appstoreconnect.apple.com](https://appstoreconnect.apple.com)
2. Navigate to your app → **TestFlight** tab
3. Wait for processing (5-30 minutes, sometimes longer for first build)
4. You'll receive an email when processing is complete
5. Once processed, your build appears under **"iOS Builds"**

### Step 7: Set Up TestFlight Testing

#### Internal Testing (Up to 100 testers, instant access)

1. In TestFlight tab, click **"Internal Testing"**
2. Click **"+"** to create a new group (e.g., "Internal Testers")
3. Add team members:
   - Click **"Add Testers"**
   - Enter email addresses of team members
   - They must have App Store Connect access
4. Select your build version
5. Click **"Start Testing"**
6. Testers receive email invitation and can install immediately

#### External Testing (Up to 10,000 testers, requires review)

1. In TestFlight tab, click **"External Testing"**
2. Click **"+"** to create a new group
3. Add testers:
   - Enter email addresses (can be anyone with an Apple ID)
   - Up to 10,000 testers per group
4. Select your build version
5. Fill in **Test Information**:
   - **What to Test**: Brief description of what testers should focus on
   - **Description**: More detailed information about the build
   - **Feedback Email**: Your email for receiving feedback
6. Click **"Submit for Review"**
7. Wait for Apple's approval (usually 24-48 hours)
8. Once approved, testers receive email invitations

### Step 8: Install on Your Device

1. Open **TestFlight** app on your iPhone
2. Accept the invitation email (if external) or the build appears automatically (if internal)
3. Tap **"Install"** next to your app
4. The app installs and you can test it!

---

## Part 2: Updating TestFlight Builds

When you've made changes to your app and want to push an update to TestFlight:

### Step 1: Update Version/Build Number

**Important**: Each TestFlight build needs a unique build number (the number after the `+`).

**Current version**: `1.0.0+1` (in `pubspec.yaml`)

**To update**:
- **Version** (e.g., `1.0.1`): Increment when you make significant changes
- **Build number** (e.g., `+2`, `+3`): Increment for every new build, even if version stays the same

**Edit `pubspec.yaml`**:
```yaml
version: 1.0.1+2  # Increment version and/or build number
```

### Step 2: Clean and Build

```bash
# Navigate to project root
cd /Users/petemcpherson/Coding\ Projects/yeet_my_pics

# Clean previous builds
flutter clean

# Get dependencies (if you added any)
flutter pub get

# Build new release
flutter build ipa
```

### Step 3: Upload New Build

**Using Xcode**:
1. Open `ios/Runner.xcworkspace` in Xcode
2. Select **Product** → **Archive**
3. Wait for archive to complete
4. In Organizer, select your new archive
5. Click **"Distribute App"**
6. Choose **"App Store Connect"** → **"Upload"**
7. Follow prompts and upload

**Using Flutter CLI + Transporter**:
1. Build with `flutter build ipa`
2. Open Transporter app
3. Drag new `.ipa` from `build/ios/ipa/` into Transporter
4. Click **"Deliver"**

### Step 4: Process and Test

1. Go to App Store Connect → Your App → **TestFlight** tab
2. Wait for processing (usually faster than first build, 5-15 minutes)
3. Once processed, the new build appears in your build list
4. **Update your test groups**:
   - Go to Internal/External Testing
   - Select your test group
   - Click **"+"** next to builds or edit existing
   - Select the new build version
   - Click **"Save"** or **"Start Testing"**

---

## Important Notes & Best Practices

### Version Numbering
- **Version format**: `MAJOR.MINOR.PATCH+BUILD`
  - `MAJOR.MINOR.PATCH`: User-facing version (e.g., `1.0.0`)
  - `BUILD`: Internal build number (e.g., `+1`, `+2`)
- **Build numbers must always increment** - Apple rejects builds with duplicate or lower build numbers
- **Version can stay the same** - You can have `1.0.0+1`, `1.0.0+2`, `1.0.0+3` etc.

### Build Processing Times
- **First build**: 30-60 minutes (sometimes longer)
- **Subsequent builds**: 5-15 minutes typically
- **Processing happens server-side** - You'll get an email when complete

### Common Issues & Solutions

**Issue**: "Bundle identifier already exists"
- **Solution**: The app already exists in App Store Connect. Skip Step 3 and go directly to uploading builds.

**Issue**: "Invalid bundle identifier"
- **Solution**: Make sure bundle ID in Xcode matches exactly what's registered in App Store Connect.

**Issue**: "Build number already in use"
- **Solution**: Increment the build number in `pubspec.yaml` and rebuild.

**Issue**: "Missing compliance"
- **Solution**: In App Store Connect → App Information → Answer export compliance questions (usually "No" for most apps).

**Issue**: Upload fails
- **Solution**: Check your internet connection, try again. Sometimes Xcode's upload is more reliable than Transporter.

### Permissions Already Configured

Your app already has the required permissions in `ios/Runner/Info.plist`:
- ✅ `NSPhotoLibraryUsageDescription`
- ✅ `NSPhotoLibraryAddUsageDescription`
- ✅ `PHPhotoLibraryPreventAutomaticLimitedAccessAlert`

### Quick Reference Commands

```bash
# Clean build artifacts
flutter clean

# Get/update dependencies
flutter pub get

# Build iOS release
flutter build ipa

# Open Xcode workspace
open ios/Runner.xcworkspace

# Check Flutter version
flutter --version

# Run analyzer
flutter analyze
```

---

## Summary Workflow

### Initial Launch
1. Configure Xcode signing
2. Create app in App Store Connect
3. Build with `flutter build ipa`
4. Upload via Xcode Organizer or Transporter
5. Wait for processing
6. Set up test groups
7. Start testing!

### Updates
1. Increment version/build in `pubspec.yaml`
2. `flutter clean && flutter build ipa`
3. Upload new build
4. Wait for processing
5. Update test groups with new build
6. Testers update via TestFlight app

---

## Part 3: App Store Submission (Public Release)

Once you've tested your app via TestFlight and are ready to release publicly:

### Step 1: Upload Your Build

If you haven't already, upload a build using the same process as TestFlight:

```bash
flutter clean && flutter build ipa
```

Then deliver via Transporter. The build will be available for both TestFlight AND App Store submission.

### Step 2: Navigate to App Store Tab

1. Go to [appstoreconnect.apple.com](https://appstoreconnect.apple.com)
2. Click **My Apps** → Select **Yeet My Pics**
3. Click the **App Store** tab (not TestFlight)

### Step 3: Complete App Information

You must fill out all required fields before submitting:

#### Version Information
- **Screenshots** (required) - iPhone screenshots for each device size
  - 6.7" display (iPhone 14 Pro Max, 15 Pro Max)
  - 6.5" display (iPhone 11 Pro Max, XS Max)
  - 5.5" display (iPhone 8 Plus, 7 Plus)
  - Optional: iPad screenshots if supporting iPad
- **Promotional Text** (optional) - Can be updated without new build
- **Description** (required) - Full app description for store listing
- **Keywords** - Search terms (100 character limit, comma-separated)
- **Support URL** (required) - Link to support page/website
- **Marketing URL** (optional) - Link to marketing website

#### App Review Information
- **Contact Info** - Phone and email for Apple reviewers
- **Sign-in Required?** - If login needed, provide demo credentials
- **Notes for Reviewer** - Explain anything reviewers should know

#### General App Information
- **Privacy Policy URL** (required for apps with IAP/user data)
- **Age Rating** - Complete Apple's questionnaire
- **Copyright** - e.g., "2024 Your Name"
- **Primary Category** - Choose most relevant category
- **Secondary Category** (optional)

### Step 4: Select Your Build

1. Scroll to the **Build** section
2. Click **"+"** or **"Select a build"**
3. Choose your processed build (e.g., `1.0.0+3`)
4. If build doesn't appear, wait for processing to complete

### Step 5: Set Up Pricing

1. Go to **App Store** → **Pricing and Availability**
2. Set your price tier (or Free if using IAP only)
3. Select available countries/regions
4. Configure any price schedules if needed

### Step 6: Submit In-App Purchases (If Applicable)

**Important**: Your IAP must be submitted alongside the app.

1. Go to **Features** → **In-App Purchases**
2. Verify `com.yeetmypics.premium_unlock` is configured
3. Ensure status is **"Ready to Submit"**
4. IAP will be reviewed with your app

### Step 7: Submit for Review

1. Verify all required fields are complete (no red warnings/errors)
2. Click **"Add for Review"** (top right corner)
3. Answer any compliance questions:
   - **Export Compliance**: Usually "No" for most apps
   - **Content Rights**: Confirm you have rights to all content
   - **Advertising Identifier**: "No" unless using IDFA
4. Click **"Submit to App Review"**

### Step 8: Wait for Review

- **Typical review time**: 24-48 hours (can vary)
- **Status updates**: You'll receive emails for status changes
- **Possible outcomes**:
  - ✅ **Approved** - App goes live (or scheduled date)
  - ❌ **Rejected** - Apple provides reasons; fix and resubmit
  - ⏸️ **In Review** - Currently being reviewed
  - 🔄 **Metadata Rejected** - Only store listing info needs fixes

### App Store Submission Checklist

Before clicking submit:
- [ ] All screenshots uploaded (required sizes)
- [x] App description written and proofread
- [x] Keywords optimized for discoverability
- [x] Support URL provided and working
- [x] Privacy Policy URL provided (required for IAP)
- [ ] Age rating questionnaire completed
- [ ] Build selected
- [x] Pricing configured
- [x] In-App Purchases ready to submit (if applicable)
- [x] Export compliance answered
- [x] Contact info for reviewers provided

### Common Rejection Reasons

**Issue**: Missing Privacy Policy
- **Solution**: Create and host a privacy policy, add URL in App Store Connect

**Issue**: Broken links
- **Solution**: Verify Support URL and Privacy Policy URL work

**Issue**: Incomplete metadata
- **Solution**: Fill in all required fields, add screenshots

**Issue**: Guideline violations
- **Solution**: Read rejection reason carefully, make required changes, resubmit

**Issue**: IAP issues
- **Solution**: Ensure IAP is properly configured and "Ready to Submit"

### After Approval

Once approved:
1. App automatically goes live (unless you set a manual release date)
2. May take a few hours to appear in App Store search
3. Monitor reviews and ratings
4. Plan your first update based on user feedback