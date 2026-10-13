# MAD Practical 5: Login & Registration Screens with Jetpack Compose

## 🎯 Aim
Create an Android Application that includes **Login** and **Registration** screens using **Jetpack Compose** and **Jetpack Navigation Compose**.

---

## 📱 App Overview & Architecture

This application demonstrates modern Android UI development using **Jetpack Compose** (Material 3) adhering to Unidirectional Data Flow (UDF) state hoisting principles. The app provides a smooth, declarative transition between authentication flows (Login and Registration) with robust input validation and reusable components.

---

## 📁 Detailed Project Structure

```text
app/src/main/java/com/example/a24012011117_mad_practical_5/
├── MainActivity.kt         # Entry point activity initializing Edge-to-Edge and setContent
├── AppNavigation.kt        # Navigation graph setup (NavHost, composable routes)
├── LoginScreen.kt          # Login UI with Email, Password, Forgot Password, and Sign Up links
├── RegisterScreen.kt       # Registration UI with Name, Phone, City, Email, Password, Confirm Password
├── FormField.kt            # Highly reusable form input field supporting validation & types
└── ui/theme/               # Material 3 Design System Styling
    ├── Color.kt            # Custom color palettes (Purple80, Pink40, etc.)
    ├── Theme.kt            # Dynamic color support (Android 12+) and dark/light palettes
    └── Type.kt             # Material 3 typography and text styles
```

---

## ⚙️ Key Jetpack Compose Components & APIs Used

1. **`NavHost` & `rememberNavController()`**:
   - Manages navigation state across screens (`login` and `register` routes) without fragment boilerplate.
2. **`OutlinedTextField`**:
   - Provides Material 3 outlined input boxes for user data entry with built-in labels and single-line constraints.
3. **`PasswordVisualTransformation` & `KeyboardOptions`**:
   - Secures password text input and optimizes the on-screen software keyboard (e.g., `KeyboardType.Password`, `KeyboardType.Number`, `KeyboardType.Email`).
4. **`Card` & `CardDefaults`**:
   - Wraps form inputs inside elevated cards (`defaultElevation = 20.dp`) with medium rounded corners (`MaterialTheme.shapes.medium`).
5. **`verticalScroll(rememberScrollState())`**:
   - Ensures forms remain fully accessible and scrollable on smaller screens or when the software keyboard is active (`adjustResize`).
6. **State Hoisting (`mutableStateOf` & `remember`)**:
   - Manages text field states reactively across user interactions.

---

## 🚀 Detailed Working & User Flow

### 1. **Launch & Navigation Setup (`MainActivity.kt` & `AppNavigation.kt`)**
- `MainActivity` sets up Edge-to-Edge display (`enableEdgeToEdge()`) and hosts `AppNavigation`.
- `AppNavigation` defines the navigation graph:
  - **Start Destination**: `"login"`
  - **Routes**:
    - `"login"` ➔ Navigates to `LoginScreen`
    - `"register"` ➔ Navigates to `RegisterScreen`

### 2. **Login Screen (`LoginScreen.kt`)**
- Displays the university/app logo image (`guni_pink_logo`).
- Contains a form card with:
  - Email input field.
  - Password input field (masked).
  - "Forgot Password" text action.
  - Primary "Login" button (triggers a Toast notification on click).
- Bottom row provides navigation to the Registration screen when tapping **"Don't Have an Account?"** or **"SIGN UP"**.

### 3. **Registration Screen (`RegisterScreen.kt`)**
- Contains an expanded form card for new user onboarding:
  - Full Name, Phone Number (with numeric digit filtering), City, Email, Password, and Confirm Password.
- Primary "Register" button triggers a Toast notification.
- Bottom row allows returning to the Login screen via **"Already Have an Account?"** or **"Login"**.

---

## 💻 Code Implementation Highlights

### Reusable Form Field (`FormField.kt`)
```kotlin
@Composable
fun FormField(
    label: String,
    textState: String,
    onTextChange: (String) -> Unit,
    isPasswordField: Boolean = false,
    isNumber: Boolean = false
) {
    Row(
        modifier = Modifier
            .fillMaxWidth()
            .padding(vertical = 6.dp),
        horizontalArrangement = Arrangement.SpaceBetween,
        verticalAlignment = Alignment.CenterVertically
    ) {
        Text(text = label, fontSize = 16.sp, modifier = Modifier.weight(0.9f))

        OutlinedTextField(
            value = textState,
            onValueChange = { newValue ->
                if (!isNumber || newValue.all { it.isDigit() }) {
                    onTextChange(newValue)
                }
            },
            modifier = Modifier.weight(1.6f).height(60.dp),
            visualTransformation = if (isPasswordField) PasswordVisualTransformation() else VisualTransformation.None,
            singleLine = true,
            keyboardOptions = KeyboardOptions(
                keyboardType = when {
                    isPasswordField -> KeyboardType.Password
                    isNumber -> KeyboardType.Number
                    label == "Email" -> KeyboardType.Email
                    else -> KeyboardType.Text
                }
            )
        )
    }
}
```

---

## 🛠️ How to Build and Run

1. Open the project in **Android Studio** (Koala / Ladybug or newer).
2. Ensure Gradle sync is completed successfully.
3. Connect an Android device or start an Android Emulator (API 24+).
4. Click **Run (`▶`)** or execute the build task via Gradle:
   ```bash
   ./gradlew assembleDebug
   ```

---

## 🛠️ Tech Stack & Requirements

- **Language**: Kotlin 2.0+
- **UI Toolkit**: Jetpack Compose (Material 3)
- **Navigation**: Jetpack Navigation Compose (2.8+)
- **Build System**: Gradle 9.5 / AGP 8.7+
- **Minimum SDK**: API 24 (Android 7.0 Nougat)
- **Target SDK**: API 35 (Android 15)
