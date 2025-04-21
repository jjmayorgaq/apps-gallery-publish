
# 🏦 React Native CLI - App Bancaria para Huawei AppGallery

Este proyecto es una aplicación móvil bancaria desarrollada con **React Native CLI** y adaptada para ser publicada en **Huawei AppGallery**, permitiendo a usuarios de dispositivos Huawei acceder a servicios financieros de forma segura.

---

## 🚀 Características principales

- App financiera desarrollada con React Native CLI
- Compatible con dispositivos Huawei sin servicios de Google (GMS)
- Configurada con AppGallery Connect
- Preparada para publicación con `APK` o `AAB` firmados
- Seguridad y privacidad priorizadas

---

## 🛠️ Requisitos

- Node.js >= 14
- React Native CLI
- Android Studio
- Cuenta de desarrollador en [Huawei Developer Center](https://developer.huawei.com/)
- Proyecto creado en [AppGallery Connect](https://developer.huawei.com/consumer/en/service/josp/agc/index.html)
- Certificado digital de firma (keystore)

---

## 🔧 Configuración para AppGallery

### 1. Integrar AppGallery Connect

- Descarga `agconnect-services.json` desde AppGallery Connect
- Colócalo en `android/app/agconnect-services.json`

### 2. Modifica `android/build.gradle`

```gradle
buildscript {
    repositories {
        google()
        mavenCentral()
        maven { url 'https://developer.huawei.com/repo/' }
    }
    dependencies {
        classpath 'com.huawei.agconnect:agcp:1.9.1.300'
    }
}
```

### 3. Modifica `android/app/build.gradle`

```gradle
apply plugin: 'com.huawei.agconnect'
```

---

## 📦 Generar APK o AAB

```bash
cd android
./gradlew assembleRelease     # Para APK
./gradlew bundleRelease       # Para AAB (recomendado)
```

---

## 📤 Publicación en Huawei AppGallery

1. Inicia sesión en AppGallery Connect
2. Crea una nueva app → completa información (nombre, descripción, región, etc.)
3. Sube tu archivo `.aab` o `.apk` firmado
4. Agrega capturas, íconos, política de privacidad
5. Enviar a revisión

---

## 🔐 Consideraciones de Seguridad y Cumplimiento

- **Cumplimiento financiero**: asegúrate de cumplir con normativas locales y regulaciones como PCI-DSS, ISO/IEC 27001, etc.
- **Uso de HTTPS obligatorio** para todas las comunicaciones con backend.
- **Firmado seguro de APK** y **proguard activado** para ofuscación del código.
- **Cifrado de datos sensibles** (PIN, tokens, claves) tanto en tránsito como en reposo.
- **Integración con HMS Core (si aplica)**:
  - Push Kit para notificaciones
  - Safety Detect para verificar integridad del dispositivo
  - Awareness Kit (opcional para contexto de usuario)

---

## 🧩 Compatibilidad sin Google Services

Huawei no incluye GMS (Google Mobile Services), por lo tanto:

| Funcionalidad | Alternativa Huawei         |
|---------------|-----------------------------|
| Google Maps   | Huawei Map Kit (o WebView) |
| Firebase Push | Huawei Push Kit             |
| Play Services | HMS Core SDK                |
| App Signing   | AppGallery Connect          |

---

## 💰 Costos

- Cuenta de desarrollador: **Gratis**
- Publicar la app: **Gratis**
- Promoción: Opcional (modelo CPD)

---

## 🧪 Recomendaciones para Testing

- Usar dispositivos Huawei reales (con HMS) para pruebas
- Pruebas de seguridad, autenticación y flujos de error
- Validación de sesiones, logout seguro, y caducidad de tokens

---

## 📄 Licencia

Este proyecto está licenciado bajo MIT.
