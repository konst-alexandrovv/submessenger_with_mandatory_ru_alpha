# Защищенный sub'мессенджер pre-Alpha version

This project have only russian localization!

Кроссплатформенный sub'мессенджер с GPG шифрованием и мандатным управлением доступом.

![Лицензия](https://img.shields.io/badge/license-GPL--3.0-blue.svg)

## Возможности

- GPG шифрование сообщений и файлов
- Мандатное управление доступом (MAC) с поддержкой уровней и категорий
- Групповое шифрование с динамическим управлением ключами
- Поддержка всех основных платформ (Web, Desktop, Mobile)
- Интеграция с Telegram Mini App

## Требования

- Node.js 20+
- npm 10+
- JDK 11+ (для Android)
- Java 17+
- Xcode 13+ (для iOS)
- Android Studio (для Android)
- Visual Studio Build Tools 2019+ (для Windows)
- wine (i386/wine32;wine64) (для Windows из Linux)

## Карта проекта

```
.
├── Dockerfile
├── README.md
├── android
│   └── app
│       └── build.gradle
├── capacitor.config.ts
├── docker-compose.yml
├── electron
│   ├── forge.config.js
│   ├── main.js
│   └── preload.js
├── electron-builder.json
├── global.d.ts
├── index.html
├── ios
│   └── App
│       └── App.xcconfig
├── nginx.conf
├── package.json
├── public
│   └── manifest.json
├── scripts
│   ├── build-all.sh
│   └── deploy.sh
├── src
│   ├── components
│   │   ├── AdvancedSecuritySettings.tsx
│   │   ├── AppLayout.tsx
│   │   ├── ConfirmDialog.tsx
│   │   ├── ErrorBoundary.tsx
│   │   ├── FilePanel.tsx
│   │   ├── GroupPanel.tsx
│   │   ├── KeyPanel.tsx
│   │   ├── MandatoryAccessControl.tsx
│   │   ├── MessagePanel.tsx
│   │   ├── PassphraseDialog.tsx
│   │   ├── Progress.tsx
│   │   ├── SecurityBadge.tsx
│   │   ├── SimpleSecuritySettings.tsx
│   │   ├── ThemeToggle.tsx
│   │   ├── security
│   │   │   └── PasswordManager.tsx
│   │   └── ui
│   │       ├── index.ts
│   │       └── primitives
│   │           ├── README.md
│   │           ├── alert.tsx
│   │           ├── button.tsx
│   │           ├── card.tsx
│   │           ├── checkbox.tsx
│   │           ├── dialog-trigger.tsx
│   │           ├── dialog.tsx
│   │           ├── dropdown-menu.tsx
│   │           ├── input.tsx
│   │           ├── label.tsx
│   │           ├── radio-group.tsx
│   │           ├── select.tsx
│   │           ├── slider.tsx
│   │           ├── switch.tsx
│   │           ├── tabs.tsx
│   │           ├── textarea.tsx
│   │           ├── toast.tsx
│   │           └── use-toast.tsx
│   ├── config
│   │   ├── localization.ts
│   │   └── security.ts
│   ├── contexts
│   │   └── ThemeContext.tsx
│   ├── global.d.ts
│   ├── hooks
│   │   ├── useKeyboardShortcuts.ts
│   │   └── useToast.ts
│   ├── main.tsx
│   ├── stores
│   │   ├── keyStore.ts
│   │   └── securityStore.ts
│   ├── types
│   │   ├── security.ts
│   │   └── ui.ts
│   └── utils
│       ├── cn.ts
│       ├── crypto.ts
│       ├── securityHelpers.ts
│       ├── ui.ts
│       └── validation.ts
├── styles
│   └── global.css
├── tailwind.config.ts
├── tsconfig.json
├── tsconfig.node.json
├── vite.config.ts
└── workbox-config.js
```

## Быстрый старт

```bash
git clone https://github.com/your-org/secure-subessenger.git
cd secure-submessenger
chmod +x ./scripts/build-all.sh
./scripts/build-all.sh
```

## Сборка

### Веб-версия
```bash
npm run build:web
```
Результат: `dist/`

### PWA
```bash
npm run build:pwa
```
Результат: `dist/` с service worker

### Десктоп (Electron)

```bash
# Windows
npm run build:electron -- --win
# Результат: dist_electron/win-unpacked/

# macOS
export APPLE_ID="your.email@example.com"
export APPLE_ID_PASSWORD="app-specific-password"
export APPLE_TEAM_ID="team-id"
npm run build:electron -- --mac
# Результат: dist_electron/mac/

# Linux
npm run build:electron -- --linux
# Результат: dist_electron/linux-unpacked/
```

### Мобильные приложения

#### Android
```bash
# Создание keystore
keytool -genkey -v -keystore release.keystore -alias key0 -keyalg RSA -keysize 2048 -validity 10000

# Сборка
export KEYSTORE_PASSWORD="your-password"
export KEY_PASSWORD="your-password"
npx cap add android
chmod +x android/gradlew
npm run build:android
```
Результат: `android/app/build/outputs/apk/release/`

#### iOS
```bash
npm run build:ios
```
Результат: `ios/App/build/`

### Docker
```bash
docker-compose up -d --build
```

## Разработка

```bash
npm run dev         # Запуск сервера разработки
npm run preview    # Предпросмотр production сборки
```

## Безопасность

### Уровни доступа

| Уровень           | ID | Категории | Целостность |
|------------------|---:|----------:|------------:|
| Публичный        |  0 |     0x00  |      0x00   |
| Внутренний       |  1 |     0x01  |      0x03   |
| Конфиденциальный |  2 |     0x03  |      0x07   |
| Секретный        |  3 |     0x07  |      0x0F   |

### Функции безопасности

- End-to-end шифрование сообщений и файлов
- Управление криптографическими ключами
- Поддержка групповых ключей с возможностью ротации
- Мандатный контроль доступа
- Двухфакторная аутентификация
- Безопасное хранение паролей
- Расширенный журнал аудита

## Лицензия

Help in creating and review with Claude 3.5

[GNU GPL v3](LICENSE)

---

# Secure Sub'Messenger pre-Alpha version

This project have only russian localization!

Cross-platform sub'messenger with GPG encryption and mandatory access control.

![License](https://img.shields.io/badge/license-GPL--3.0-blue.svg)

## Features

- GPG encryption for messages and files
- Mandatory Access Control (MAC) with levels and categories
- Group encryption with dynamic key management
- Support for all major platforms (Web, Desktop, Mobile)
- Telegram Mini App integration

## Requirements

- Node.js 20+
- npm 10+
- JDK 11+ (for Android)
- Java 17+
- Xcode 13+ (for iOS)
- Android Studio (for Android)
- Visual Studio Build Tools 2019+ (for Windows)
- wine (i386/wine32;wine64) (for Windows from Linux)

## Map of project

```
.
├── Dockerfile
├── README.md
├── android
│   └── app
│       └── build.gradle
├── capacitor.config.ts
├── docker-compose.yml
├── electron
│   ├── forge.config.js
│   ├── main.js
│   └── preload.js
├── electron-builder.json
├── global.d.ts
├── index.html
├── ios
│   └── App
│       └── App.xcconfig
├── nginx.conf
├── package.json
├── public
│   └── manifest.json
├── scripts
│   ├── build-all.sh
│   └── deploy.sh
├── src
│   ├── components
│   │   ├── AdvancedSecuritySettings.tsx
│   │   ├── AppLayout.tsx
│   │   ├── ConfirmDialog.tsx
│   │   ├── ErrorBoundary.tsx
│   │   ├── FilePanel.tsx
│   │   ├── GroupPanel.tsx
│   │   ├── KeyPanel.tsx
│   │   ├── MandatoryAccessControl.tsx
│   │   ├── MessagePanel.tsx
│   │   ├── PassphraseDialog.tsx
│   │   ├── Progress.tsx
│   │   ├── SecurityBadge.tsx
│   │   ├── SimpleSecuritySettings.tsx
│   │   ├── ThemeToggle.tsx
│   │   ├── security
│   │   │   └── PasswordManager.tsx
│   │   └── ui
│   │       ├── index.ts
│   │       └── primitives
│   │           ├── README.md
│   │           ├── alert.tsx
│   │           ├── button.tsx
│   │           ├── card.tsx
│   │           ├── checkbox.tsx
│   │           ├── dialog-trigger.tsx
│   │           ├── dialog.tsx
│   │           ├── dropdown-menu.tsx
│   │           ├── input.tsx
│   │           ├── label.tsx
│   │           ├── radio-group.tsx
│   │           ├── select.tsx
│   │           ├── slider.tsx
│   │           ├── switch.tsx
│   │           ├── tabs.tsx
│   │           ├── textarea.tsx
│   │           ├── toast.tsx
│   │           └── use-toast.tsx
│   ├── config
│   │   ├── localization.ts
│   │   └── security.ts
│   ├── contexts
│   │   └── ThemeContext.tsx
│   ├── global.d.ts
│   ├── hooks
│   │   ├── useKeyboardShortcuts.ts
│   │   └── useToast.ts
│   ├── main.tsx
│   ├── stores
│   │   ├── keyStore.ts
│   │   └── securityStore.ts
│   ├── types
│   │   ├── security.ts
│   │   └── ui.ts
│   └── utils
│       ├── cn.ts
│       ├── crypto.ts
│       ├── securityHelpers.ts
│       ├── ui.ts
│       └── validation.ts
├── styles
│   └── global.css
├── tailwind.config.ts
├── tsconfig.json
├── tsconfig.node.json
├── vite.config.ts
└── workbox-config.js
```

## Quick Start

```bash
git clone https://github.com/your-org/secure-submessenger.git
cd secure-submessenger
chmod +x ./scripts/build-all.sh
./scripts/build-all.sh
```

## Building

### Web
```bash
npm run build:web
```
Output: `dist/`

### PWA
```bash
npm run build:pwa
```
Output: `dist/` with service worker

### Desktop (Electron)

```bash
# Windows
npm run build:electron -- --win
# Output: dist_electron/win-unpacked/

# macOS
export APPLE_ID="your.email@example.com"
export APPLE_ID_PASSWORD="app-specific-password"
export APPLE_TEAM_ID="team-id"
npm run build:electron -- --mac
# Output: dist_electron/mac/

# Linux
npm run build:electron -- --linux
# Output: dist_electron/linux-unpacked/
```

### Mobile Apps

#### Android
```bash
# Generate keystore
keytool -genkey -v -keystore release.keystore -alias key0 -keyalg RSA -keysize 2048 -validity 10000

# Build
export KEYSTORE_PASSWORD="your-password"
export KEY_PASSWORD="your-password"
npx cap add android
chmod +x android/gradlew
npm run build:android
```
Output: `android/app/build/outputs/apk/release/`

#### iOS
```bash
npm run build:ios
```
Output: `ios/App/build/`

### Docker
```bash
docker-compose up -d --build
```

## Development

```bash
npm run dev         # Start dev server
npm run preview    # Preview production build
```

## Security

### Access Levels

| Level        | ID | Categories | Integrity |
|-------------|---:|----------:|----------:|
| Public      |  0 |     0x00  |     0x00  |
| Internal    |  1 |     0x01  |     0x03  |
| Confidential|  2 |     0x03  |     0x07  |
| Secret      |  3 |     0x07  |     0x0F  |

### Security Features

- End-to-end message and file encryption
- Cryptographic key management
- Group key support with rotation capability
- Mandatory access control
- Two-factor authentication
- Secure password storage
- Advanced audit logging

## License

Help in creating and review with Claude 3.5

[GNU GPL v3](LICENSE)
