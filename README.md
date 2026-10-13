# MAD Practical 5: Login & Registration Screens with Jetpack Compose

## 🎯 Aim
Create an Android Application that includes **Login** and **Registration** screens using **Jetpack Compose**.

---

## 📱 Features

- **Jetpack Compose Declarative UI**: Built entirely with modern Compose components (Material 3).
- **Navigation Compose**: Seamless screen navigation between Login and Registration screens using `NavHost` and `rememberNavController`.
- **Custom Reusable Form Field**: Reusable `FormField` composable supporting:
  - Standard text inputs (Email, Name, City)
  - Number inputs (Phone Number filtering non-digit characters)
  - Password inputs (Visual transformation using `PasswordVisualTransformation` and password keyboard type)
- **Interactive Navigation**:
  - Toast feedback messages for primary actions (Login & Register).
  - Navigation links allowing quick switching between Login and Registration screens.
- **Material 3 Theme**: Complete theme setup including Colors, Typography, and Shapes.

---

## 📁 Project Structure

```text
app/src/main/java/com/example/a24012011117_mad_practical_5/
├── MainActivity.kt         # Entry activity with Edge-to-Edge display
├── AppNavigation.kt        # NavHost setup for "login" and "register" routes
├── LoginScreen.kt          # Login UI screen
├── RegisterScreen.kt       # Registration UI screen
├── FormField.kt            # Custom reusable input field composable
└── ui/theme/               # Material 3 Design Theme
    ├── Color.kt            # Custom Color palettes
    ├── Theme.kt            # MaterialTheme configuration
    └── Type.kt             # Typography configurations
```

---

## ⚙️ Key Jetpack Compose Components Used

1. **`NavHost` & `rememberNavController`**: Manages app navigation state and screen transitions.
2. **`OutlinedTextField`**: Outlined input text fields for user entries.
3. **`Card` & `CardDefaults`**: Container card with elevation to group form inputs neatly.
4. **`Button` & `TextButton`**: Primary action buttons and navigation links.
5. **`Column` & `Row`**: Layout composables with scrolling (`verticalScroll`) and alignment.
6. **`PasswordVisualTransformation`**: Obfuscates password input for privacy.
7. **`KeyboardOptions`**: Adapts soft keyboard layout based on input type (e.g., `KeyboardType.Email`, `KeyboardType.Number`, `KeyboardType.Password`).

---

## 🚀 How It Works

1. **Launch**: The application starts on the **Login Screen** (`login` route).
2. **Login Screen**:
   - Accepts Email and Password inputs.
   - Tapping **"Login"** displays a Toast confirmation message.
   - Tapping **"Don't Have an Account?"** or **"SIGN UP"** navigates to the **Registration Screen**.
3. **Registration Screen**:
   - Accepts Name, Phone Number, City, Email, Password, and Confirm Password.
   - Tapping **"Register"** displays a Toast confirmation message.
   - Tapping **"Already Have an Account?"** or **"Login"** navigates back to the **Login Screen**.

---

## 🛠️ Tech Stack & Requirements

- **Language**: Kotlin
- **UI Toolkit**: Jetpack Compose (Material 3)
- **Navigation**: Jetpack Navigation Compose
- **Minimum SDK**: API 24 (Android 7.0)
- **Target SDK**: API 35
