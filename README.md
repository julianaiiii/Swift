# Cloud Calorie Tracker — Codemagic-ready SwiftUI project

This repository contains a native iPhone app built with SwiftUI + SwiftData, prepared for CloudKit sync and Codemagic cloud builds.

## Fastest build without a Mac

1. Create a GitHub repository and upload the contents of this folder.
2. In Codemagic, add the repository as an application.
3. Choose the **ios-simulator** workflow from `codemagic.yaml`.
4. Start the build.
5. Download `CloudCalorieTracker-Simulator.zip` from the build artifacts.

The simulator workflow does not require Apple code signing.

## Before using CloudKit on a real signed app

The project currently uses the placeholder bundle identifier:

`com.example.CloudCalorieTracker`

Change it to a bundle ID you own in both:

- `CloudCalorieTracker.xcodeproj/project.pbxproj`
- `codemagic.yaml`

The CloudKit entitlement is configured as:

`iCloud.$(PRODUCT_BUNDLE_IDENTIFIER)`

For a production build, create/enable the corresponding iCloud container for the App ID in your Apple Developer account.

## Signed IPA / TestFlight

The `ios-app-store` workflow is included as a template. Before running it:

1. Join/use an Apple Developer Program team.
2. Create the final App ID and enable iCloud/CloudKit.
3. Create an app record in App Store Connect.
4. Add an App Store Connect integration in Codemagic named `codemagic`, or update the integration name in `codemagic.yaml`.
5. Make sure Codemagic can fetch an App Store distribution certificate and provisioning profile matching your final bundle ID.
6. Update `bundle_identifier` in `codemagic.yaml`.

Then run **ios-app-store** to create the `.ipa`.

## Included app features

- Native SwiftUI interface
- SwiftData models
- CloudKit-ready model configuration
- Daily calorie goal
- Log breakfast, lunch, dinner, and snacks
- Today's calorie progress
- History grouped by date
- CloudKit entitlements
- Shared Xcode scheme
- Codemagic simulator workflow
- Codemagic signed IPA workflow template

## Files

- `CloudCalorieTracker.xcodeproj` — Xcode project
- `CloudCalorieTracker/` — Swift source and assets
- `codemagic.yaml` — cloud build workflows
- `.gitignore`

## Note

The project structure and configuration were assembled outside macOS, so the Xcode project itself has not been launched in Xcode in this environment. The Codemagic simulator workflow is the intended first validation step.
