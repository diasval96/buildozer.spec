# 📜 README – Arquivo `buildozer.spec`

## 📖 Sobre
O `buildozer.spec` é o arquivo de configuração usado pelo **Buildozer** para compilar aplicativos Python em APKs Android.  
Ele define nome do app, dependências, permissões, arquitetura e recursos de hardware que o app vai usar.

Este modelo já vem otimizado para:
- **Apps em Python/Kivy/KivyMD**  
- **Suporte a sensores via Plyer**  
- **Permissões Android comuns** (internet, câmera, GPS, vibração, áudio, armazenamento)  
- **Arquitetura arm64-v8a** (a maioria dos celulares modernos)  

---

## ⚙️ Estrutura do arquivo

### 📦 Informações básicas
```ini
title = MeuApp
package.name = meuapp
package.domain = org.dias.accessx
version = 0.1
```
- **title** → Nome do app exibido no celular  
- **package.name** → Nome interno do pacote  
- **package.domain** → Domínio reverso (único para cada app)  
- **version** → Versão inicial do app  

---

### 🐍 Dependências Python
```ini
requirements = python3,kivy,kivymd,flask,plyer,cython
```
- **kivy** → interface gráfica  
- **kivymd** → Material Design para Kivy  
- **flask** → backend local  
- **plyer** → acesso a sensores (GPS, câmera, bateria, vibração)  
- **cython** → otimização de performance  

---

### 🔑 Permissões Android
```ini
android.permissions = INTERNET,WRITE_EXTERNAL_STORAGE,READ_EXTERNAL_STORAGE,CAMERA,ACCESS_FINE_LOCATION,VIBRATE,RECORD_AUDIO
```
- **INTERNET** → acesso à rede  
- **WRITE/READ_EXTERNAL_STORAGE** → salvar/ler arquivos  
- **CAMERA** → tirar fotos  
- **ACCESS_FINE_LOCATION** → GPS  
- **VIBRATE** → vibração  
- **RECORD_AUDIO** → microfone  

---

### 📱 Arquitetura e SDK/NDK
```ini
android.arch = arm64-v8a
android.api = 33
android.minapi = 24
android.sdk = 24
android.ndk = 23b
android.build_tools = 33.0.2
```
- **arm64-v8a** → arquitetura padrão dos celulares modernos  
- **api 33** → Android 13 como alvo  
- **minapi 24** → Android 7.0 como mínimo  
- **sdk/ndk/build_tools** → versões fixas para evitar downloads múltiplos  

---

### 🎨 Recursos visuais
```ini
icon.filename = %(source.dir)s/assets/icon.png
presplash.filename = %(source.dir)s/assets/splash.png
```
- **icon.png** → ícone do app  
- **splash.png** → tela inicial  

---

### 🔧 Configuração extra
```ini
p4a.branch = master
p4a.bootstrap = sdl2
log_level = 2
cython = True
```
- **bootstrap sdl2** → necessário para apps Kivy  
- **log_level 2** → ativa logs para debug  
- **cython True** → otimização de código  

---

## 🚀 Como usar
1. Crie o projeto com:
   ```bash
   buildozer init
   ```
2. Substitua o arquivo `buildozer.spec` pelo modelo otimizado.
   ```bash
   [app]
   title = MeuApp
   package.name = meuapp
   package.domain = org.dias.accessx
   version = 0.1
   source.dir = .
   requirements = python3,kivy,kivymd,flask,plyer,cython
   android.permissions = INTERNET,WRITE_EXTERNAL_STORAGE,READ_EXTERNAL_STORAGE,CAMERA,ACCESS_FINE_LOCATION,VIBRATE,RECORD_AUDIO
   orientation = all
   icon.filename = %(source.dir)s/assets/icon.png
   presplash.filename = %(source.dir)s/assets/splash.png
   android.arch = arm64-v8a
   android.api = 33
   android.minapi = 24
   android.sdk = 24
   android.ndk = 23b
   android.build_tools = 33.0.2
   log_level = 2
   p4a.branch = master
   p4a.bootstrap = sdl2
   cython = True
   
    ``` 
5. Compile o APK:
   ```bash
   buildozer -v android debug
   ```
6. Instale no celular:
   ```bash
   pm install bin/*.apk
   ```
