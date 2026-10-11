# Homework 6 — My First Compose App

## Task 3: Colour and Spacing
Colour used: `Color.Magenta`
Padding kept: `24.dp`
What changed / what stayed the same: Changing the padding value from 8 dp to 48 dp increases the inner spacing surrounding the content (the texts and image) relative to the screen edges, pushing all elements closer to the center. However, the background color applied by the Surface and the size of the inner UI components remain the same regardless of the padding size.

## Task 4: Build Error
First error message: `File name 'My-Picture.jpeg' is not a valid resource name. File-based resource names must contain only lowercase a-z, 0-9, or underscores.`
Cause: Android resource naming rules dictate that resource files in the `drawable` directory must strictly consist of lowercase letters (`a-z`), digits (`0-9`), and underscores (`_`). Renaming the file to `My-Picture.jpeg` violates this rule because it contains uppercase letters and a hyphen (`-`).
Why other errors appear: Secondary errors like `unresolved reference: my_picture` appear because Android Studio fails to compile the invalid resource file and cannot generate its corresponding ID in the `R` class (`R.drawable.my_picture`). As a result, Kotlin code referencing `R.drawable.my_picture` cannot find the identifier during compilation.
Fix: Rename the image file back to `my_picture.jpeg` (or `my_picture.png`) using only valid characters (lowercase letters and underscores) and rebuild the project.

## Task 5: Explore the Project
(a) MainActivity: path `app/src/main/java/com/example/myfirstcomposeapp/MainActivity.kt` — This file serves as the main entry point of the Android application where the UI components and Compose activities are defined and executed.
(b) Gradle file: path `app/build.gradle.kts` — This file defines module-level build configurations, dependencies, target SDK versions, and plugins required specifically for the `app` module.
(c) Launcher image line: `painter = painterResource(id = R.drawable.ic_launcher_foreground)` inside `MainActivity.kt` — This line references the default vector resource used to render the initial launcher image before it was replaced in Task 2.

## Task 6: Preview vs Run
The app on the device or emulator has not changed yet because the `@Preview` feature only renders a design mockup inside Android Studio's design editor without compiling or deploying a new APK binary to the target device. To make the changes appear on the actual device or emulator, you must click the **Run** button (or press **Shift + F10**) to build, install, and launch the updated application.

## Task 7: Views vs Compose
1. In the traditional imperative approach (Views), UI components are declared in XML layouts, and developers must manually query view objects (e.g., using `findViewById`) and call setter methods to mutate their properties when state changes. In contrast, Jetpack Compose uses a declarative approach as shown in `MyFirstScreen()`, where the UI is defined as a function of the current state; when state changes, Compose automatically re-executes (recomposes) the composable function to redraw the UI.
2.
| Composable | Package | Library layer |
|---|---|---|
| Column | `androidx.compose.foundation.layout.Column` | Foundation |
| Text | `androidx.compose.material3.Text` | Material 3 |
| Image | `androidx.compose.foundation.Image` | Foundation |