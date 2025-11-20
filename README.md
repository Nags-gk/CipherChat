# CipherChat 🔐

A secure Android SMS encryption application that enables users to send and receive encrypted text messages using AES-128 encryption. Protect your private conversations with end-to-end encryption before sending SMS messages.

## 📱 Overview

CipherChat (also known as INCOGNITO) is an Android application that provides encryption and decryption capabilities for SMS messages. The app intercepts incoming SMS messages, encrypts outgoing messages, and allows users to decrypt received encrypted messages using a shared secret key.

## ✨ Features

- **AES-128 Encryption**: Uses industry-standard AES (Advanced Encryption Standard) with 128-bit keys
- **Secure SMS Communication**: Encrypts SMS messages before sending
- **Automatic Message Interception**: Intercepts incoming encrypted SMS messages
- **Decryption Interface**: User-friendly interface to decrypt received encrypted messages
- **Message Fragmentation Support**: Handles long messages that exceed SMS character limits
- **Privacy-Focused**: Prevents encrypted messages from appearing in the default SMS inbox

## 🎯 What Problem Does It Solve?

Standard SMS messages are transmitted in plain text, making them vulnerable to interception and unauthorized access. CipherChat addresses this security concern by:

- Encrypting sensitive information before transmission
- Ensuring only the intended recipient (with the correct key) can read the message
- Providing a layer of privacy for SMS communications
- Preventing unauthorized access to message content

## 🏗️ Tech Stack

### Language & Framework
- **Java** - Primary programming language
- **Android SDK** - Android development framework
  - Min SDK Version: 19 (Android 4.4 KitKat)
  - Target SDK Version: 30 (Android 11)
  - Compile SDK Version: 30

### Build Tools
- **Gradle** - Build automation
- **Android Gradle Plugin** - v7.0+

### Key Libraries & Dependencies
- `androidx.appcompat:appcompat:1.3.0` - Android support library
- `com.google.android.material:material:1.3.0` - Material Design components
- `javax.crypto.Cipher` - Cryptographic operations
- `javax.crypto.spec.SecretKeySpec` - Secret key specification

### Testing Frameworks
- `JUnit 4` - Unit testing
- `AndroidX Test` - Android instrumentation testing
- `Espresso` - UI testing

## 🔧 Technical Skills Demonstrated

### Android Development
- Activity lifecycle management
- BroadcastReceiver implementation for SMS interception
- Intent handling and data passing between activities
- Android Manifest configuration (permissions, receivers)
- UI design with XML layouts

### Security & Cryptography
- AES-128 symmetric encryption implementation
- Key generation and management
- Secure data handling
- Encryption/decryption algorithms
- Byte array and hexadecimal conversions

### System Integration
- SMS Manager API integration
- Telephony framework usage
- System broadcast handling
- Permission management (SEND_SMS, RECEIVE_SMS)

### Software Architecture
- Separation of concerns (encryption logic, UI, SMS handling)
- Event-driven programming with BroadcastReceivers
- MVC-like architecture pattern

## 📂 Project Structure

```
CipherChat/
├── app/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/example/encdecsms/
│   │   │   │   ├── EncDecSMSActivity.java      # Main activity for sending encrypted SMS
│   │   │   │   ├── DisplaySMSActivity.java      # Activity for displaying/decrypting received SMS
│   │   │   │   └── SmsBroadCastReceiver.java    # BroadcastReceiver for intercepting SMS
│   │   │   ├── res/
│   │   │   │   ├── layout/                      # UI layout files
│   │   │   │   ├── drawable/                    # App icons and graphics
│   │   │   │   ├── values/                      # String resources, styles
│   │   │   │   └── mipmap/                      # App launcher icons
│   │   │   └── AndroidManifest.xml              # App configuration and permissions
│   │   └── androidTest/                         # Android instrumentation tests
│   │   └── test/                                # Unit tests
│   ├── build.gradle                             # App-level build configuration
│   └── proguard-rules.pro                       # ProGuard rules for code obfuscation
├── build.gradle                                 # Project-level build configuration
├── gradle.properties                            # Gradle settings
├── settings.gradle                              # Gradle project settings
└── README.md                                    # This file
```

## 🚀 How to Run This Project

### Prerequisites

1. **Android Studio** (Arctic Fox or later recommended)
   - Download from: https://developer.android.com/studio

2. **Java Development Kit (JDK)** 8 or higher
   - Verify installation: `java -version`

3. **Android SDK** with the following components:
   - Android SDK Build-Tools 30.0.3
   - Android SDK Platform 30
   - Android Emulator (for testing)

4. **Physical Android Device** (Recommended) or **Android Emulator**
   - Android 4.4 (API 19) or higher
   - SMS capabilities (physical device preferred for testing SMS features)

### Installation Steps

1. **Clone the Repository**
   ```bash
   git clone https://github.com/Nags-gk/CipherChat.git
   cd CipherChat
   ```

2. **Open in Android Studio**
   - Launch Android Studio
   - Select "Open an existing project"
   - Navigate to the cloned directory and select it
   - Wait for Gradle sync to complete

3. **Configure SDK (if needed)**
   - Go to `File > Project Structure > SDK Location`
   - Ensure the correct Android SDK path is set

4. **Build the Project**
   ```bash
   # Using Gradle command line
   ./gradlew build
   
   # Or in Android Studio
   # Build > Make Project (Ctrl+F9 / Cmd+F9)
   ```

5. **Run on Device/Emulator**
   
   **Option A: Using Android Studio**
   - Connect your Android device via USB (enable USB debugging) or start an emulator
   - Click the "Run" button (▶️) or press `Shift+F10`
   - Select your target device
   
   **Option B: Using Command Line**
   ```bash
   ./gradlew installDebug
   ```

6. **Grant Permissions**
   - After installation, the app will request SMS permissions
   - Allow "Send SMS" and "Receive SMS" permissions

### Running on Physical Device

1. Enable **Developer Options** on your Android device:
   - Go to `Settings > About Phone`
   - Tap "Build Number" 7 times

2. Enable **USB Debugging**:
   - Go to `Settings > Developer Options`
   - Enable "USB Debugging"

3. Connect device via USB and ensure it's recognized:
   ```bash
   adb devices
   ```

## 📱 How to Use

### Sending an Encrypted Message

1. Launch the **CipherChat** app
2. Enter the recipient's phone number
3. Enter a **16-character secret key** (both sender and receiver must use the same key)
4. Type your message
5. Tap "Send"
6. The app will encrypt the message and send it via SMS

### Receiving and Decrypting a Message

1. When an encrypted SMS is received, CipherChat automatically intercepts it
2. The app will open the decryption screen
3. Enter the same **16-character secret key** used by the sender
4. Tap "Submit" to decrypt and view the message

### Important Notes

- **Secret Key**: Both sender and receiver must use the same 16-character key
- **Key Exchange**: Share the secret key through a secure channel (not via SMS)
- **Key Security**: Keep your secret keys private and change them regularly
- **Compatibility**: Both users must have CipherChat installed

## 🔒 Security Considerations

### Current Implementation
- Uses **AES-128** symmetric encryption
- Requires a shared 16-character secret key
- Encrypts message content before SMS transmission

### Limitations & Recommendations

⚠️ **Important Security Notes:**

1. **Key Management**: The app uses a simple shared key approach. For production use, consider implementing:
   - Secure key exchange protocols (e.g., Diffie-Hellman)
   - Public key infrastructure (PKI)
   - Key derivation functions (KDF)

2. **Metadata Exposure**: While message content is encrypted, metadata (phone numbers, timestamps) is still visible to carriers

3. **No Forward Secrecy**: If a key is compromised, all past messages encrypted with that key are vulnerable

4. **Key Storage**: Keys are entered manually and not stored. Consider implementing secure key storage using Android Keystore

5. **Authentication**: The app doesn't verify sender identity. Consider adding message authentication codes (MAC)

### Recommended Enhancements
- Implement end-to-end encryption with public/private key pairs
- Add message authentication (HMAC)
- Implement perfect forward secrecy
- Use Android Keystore for secure key storage
- Add key rotation mechanisms

## 🧪 Testing

### Running Unit Tests
```bash
./gradlew test
```

### Running Instrumentation Tests
```bash
./gradlew connectedAndroidTest
```

### Manual Testing Checklist
- [ ] Send encrypted message to another device
- [ ] Receive and decrypt message successfully
- [ ] Test with long messages (>160 characters)
- [ ] Verify message interception works
- [ ] Test with incorrect decryption key
- [ ] Verify permissions are requested properly

## 📜 Permissions Required

```xml
<uses-permission android:name="android.permission.SEND_SMS" />
<uses-permission android:name="android.permission.RECEIVE_SMS" />
```

- **SEND_SMS**: Required to send encrypted SMS messages
- **RECEIVE_SMS**: Required to intercept incoming encrypted messages

## 🐛 Troubleshooting

### Common Issues

**Issue**: App crashes when sending message
- **Solution**: Ensure SMS permissions are granted in Settings > Apps > CipherChat > Permissions

**Issue**: Cannot decrypt received message
- **Solution**: Verify you're using the exact same 16-character key as the sender

**Issue**: Messages not being intercepted
- **Solution**: Check that RECEIVE_SMS permission is granted and the app is not being killed by battery optimization

**Issue**: Build fails with SDK errors
- **Solution**: Ensure Android SDK 30 is installed via SDK Manager

## 🔄 Future Enhancements

- [ ] Implement RSA public-key cryptography
- [ ] Add contact list integration
- [ ] Support for group messaging
- [ ] Message history with encrypted storage
- [ ] Implement key exchange protocols
- [ ] Add message authentication
- [ ] Support for multimedia messages (MMS)
- [ ] Material Design 3 UI updates
- [ ] Dark mode support
- [ ] Biometric authentication for app access

## 📄 License

This project is available for educational purposes. Please check the repository for license details.

## 👤 Author

**Nags-gk**
- GitHub: [@Nags-gk](https://github.com/Nags-gk)

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

## ⭐ Show Your Support

Give a ⭐️ if you find this project interesting or helpful!

---

**Note**: This application is intended for educational purposes and demonstrates basic encryption concepts. For production use, please implement additional security measures and follow current cryptographic best practices.
