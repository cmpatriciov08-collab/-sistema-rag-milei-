# 🚀 **DEPLOYMENT EN HUGGING FACE SPACES**

## 🎯 **GUÍA COMPLETA PASO A PASO**

### **PASO 1: Preparar el Repositorio GitHub**

#### **1.1 Crear repositorio en GitHub**
```bash
# Navegar al directorio del proyecto
cd tp3/

# Inicializar git
git init

# Agregar todos los archivos (excepto los que están en .gitignore)
git add .

# Hacer primer commit
git commit -m "Sistema RAG - Discursos de Javier Milei - Versión inicial"

# Crear repositorio en GitHub (vía web):
# 1. Ir a https://github.com
# 2. Click "New repository"
# 3. Nombre: "sistema-rag-milei"
# 4. Descripción: "Sistema RAG para análisis de discursos de Javier Milei"
# 5. Público o Privado
# 6. No marcar "Add a README file" (ya tenemos uno)
# 7. Click "Create repository"
```

#### **1.2 Conectar con GitHub**
```bash
# Agregar remote origin (reemplazar con tu URL)
git remote add origin https://github.com/tu-usuario/sistema-rag-milei.git

# Subir a GitHub
git branch -M main
git push -u origin main
```

### **PASO 2: Crear Space en Hugging Face**

#### **2.1 Crear cuenta en Hugging Face**
1. Ir a: **https://huggingface.co**
2. Crear cuenta o iniciar sesión
3. Verificar email si es necesario

#### **2.2 Crear nuevo Space**
1. Ir a: **https://huggingface.co/spaces**
2. Click **"+ Create new Space"**
3. **Configuración del Space:**
   - **Name**: `sistema-rag-milei` (o el nombre que prefieras)
   - **License**: `MIT`
   - **SDK**: Seleccionar **"Streamlit"**
   - **Hardware**: Seleccionar **"CPU basic"** (gratuito)
   - **Privacy**: Seleccionar **"Public"** (para que sea visible)
4. Click **"Create a Space"**

### **PASO 3: Configurar Deployment**

#### **3.1 Clonar repositorio en el Space**
El Space automáticamente clona desde GitHub después de crearlo.

#### **3.2 Verificar archivos necesarios**
Asegurar que tengas estos archivos en tu repositorio:
- ✅ `app.py` (aplicación principal)
- ✅ `requirements.txt` (dependencias)
- ✅ `README.md` (documentación)
- ✅ `.gitignore` (archivos a ignorar)
- ✅ Archivos del sistema RAG en `src/`

#### **3.3 Configurar secrets para API key**
1. En tu Space, ir a la pestaña **"Settings"**
2. En **"Repository secrets"**, click **"Add a secret"**
3. **Name**: `GOOGLE_API_KEY`
4. **Value**: Pegar tu API key de Google Gemini
5. Click **"Add a secret"**

### **PASO 4: Verificar Deployment**

#### **4.1 Build automático**
- Hugging Face automáticamente construye tu Space
- Puedes ver el progreso en la pestaña **"Logs"**
- Primera build puede tomar 5-10 minutos

#### **4.2 Verificar funcionamiento**
1. Cuando termine el build, ir a la pestaña **"App"**
2. Tu aplicación debería estar corriendo
3. Probar la funcionalidad básica

### **PASO 5: Configuraciones Adicionales**

#### **5.1 Verificar que no hay archivos grandes**
```bash
# Asegurar que no subiste archivos de datos pesados
# Los archivos que NO deben subirse:
# - data/vector_db/ (se regenera automáticamente)
# - data/cache/ (se regenera automáticamente)
# - .env (contiene secrets)
```

#### **5.2 Optimizar para deployment**
Tu aplicación debe manejar:
- Variables de entorno para secrets
- Creación automática de directorios necesarios
- Manejo de errores de red/API

---

## 🔧 **ARCHIVOS NECESARIOS PARA HUGGING FACE**

### **requirements.txt actualizado:**
```txt
streamlit>=1.28.0
langchain>=0.1.0
langchain-google-genai>=2.0.0
langchain-chroma>=0.1.0
chromadb>=0.4.0
sentence-transformers>=2.2.0
sentencepiece>=0.1.99
transformers>=4.35.0
torch>=2.0.0
beautifulsoup4>=4.12.0
requests>=2.31.0
pandas>=2.0.0
numpy>=1.24.0
plotly>=5.15.0
python-docx>=1.0.0
pypdf>=3.0.0
streamlit-option-menu>=0.3.0
python-dotenv>=1.0.0
psutil>=5.9.0
```

### **📁 .streamlit/config.toml**
```toml
[server]
headless = true
enableCORS = false
port = 8501

[browser]
gatherUsageStats = false

[theme]
base = "light"
primaryColor = "#1f77b4"
backgroundColor = "#ffffff"
secondaryBackgroundColor = "#f0f2f6"
textColor = "#262730"
```

---

## ⚡ **COMANDOS RÁPIDOS**

### **Preparar para deployment:**
```bash
# 1. Verificar que todo funciona localmente
python setup_streamlit.py --check

# 2. Actualizar requirements.txt (si es necesario)
pip freeze > requirements.txt

# 3. Hacer commit final
git add .
git commit -m "Ready for Hugging Face Spaces deployment"
git push
```

### **URL final del Space:**
```
https://huggingface.co/spaces/tu-usuario/sistema-rag-milei
```

---

## 🛠️ **SOLUCIÓN DE PROBLEMAS**

### **Error: "Build failed"**
- Revisar logs en la pestaña **"Logs"**
- Verificar que `requirements.txt` no tiene dependencias faltantes
- Asegurar que `app.py` existe en la raíz

### **Error: "Application failed to start"**
- Verificar que no hay errores de sintaxis en `app.py`
- Revisar que todas las importaciones funcionan
- Verificar secrets están configurados correctamente

### **Error: "ImportError"**
- Verificar que todas las dependencias están en `requirements.txt`
- Asegurar que no hay conflictos de versiones

### **API key no funciona**
- Verificar que está configurada en **Settings > Repository secrets**
- Verificar que el nombre exacto es `GOOGLE_API_KEY`
- Confirmar que la API key es válida

---

## 📊 **CARACTERÍSTICAS DE TU SPACE**

### **✅ Lo que tendrás:**
- **URL pública**: https://huggingface.co/spaces/tu-usuario/sistema-rag-milei
- **Acceso desde cualquier dispositivo**: PC, móvil, tablet
- **Funcionalidad completa**: Chat RAG, Analytics, Documentos
- **Deploy automático**: Cada commit actualiza automáticamente
- **Gratis**: 100 horas de compute al mes

### **⚡ Performance esperado:**
- **Tiempo de build**: 5-10 minutos (primera vez)
- **Tiempo de respuesta**: 2-5 segundos por consulta
- **Disponibilidad**: 24/7 online
- **Tráfico**: Hasta 1000 usuarios simultáneos

---

## 🎉 **RESULTADO FINAL**

### **URL de tu aplicación:**
```
https://huggingface.co/spaces/tu-usuario/sistema-rag-milei
```

### **✅ Checklist de deployment:**
- [ ] Repositorio subido a GitHub
- [ ] Space creado en Hugging Face
- [ ] Secrets configurados (GOOGLE_API_KEY)
- [ ] Build exitoso
- [ ] Aplicación funcionando
- [ ] Pruebas básicas realizadas

**¡Tu Sistema RAG estará disponible públicamente en Internet!** 🚀

---

## 📚 **RECURSOS ADICIONALES**

- **Documentación oficial**: https://huggingface.co/docs/spaces
- **Streamlit en HF**: https://huggingface.co/docs/spaces/build-an-app/streamlit-apps
- **Troubleshooting**: https://huggingface.co/docs/spaces/debug

**¿Listo para el deployment? ¡Es más fácil de lo que parece!** 🎯