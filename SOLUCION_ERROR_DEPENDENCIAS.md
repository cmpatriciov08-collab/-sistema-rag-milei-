# 🐛 **SOLUCIÓN AL ERROR: "No module named 'PyPDF2'"**

## 🔍 **¿QUÉ SIGNIFICA ESTE ERROR?**

```
ERROR: ❌ Error inesperado inicializando RAG: No module named 'PyPDF2'
```

**Significa**: La librería `PyPDF2` (o `pypdf`) no está instalada en tu sistema.

**Causa**: Esta librería es necesaria para procesar archivos PDF, pero no se instaló automáticamente.

---

## ✅ **SOLUCIONES INMEDIATAS (Elegir UNA)**

### **🚀 SOLUCIÓN 1: Instalación Manual (Más Rápida)**

```bash
# Navegar al directorio del proyecto
cd tp3/

# Instalar PyPDF2 y otras dependencias faltantes
pip install PyPDF2 pypdf python-docx streamlit-option-menu

# Ejecutar el sistema
python setup_streamlit.py --init-only
```

### **🔧 SOLUCIÓN 2: Actualizar Requirements (Recomendada)**

```bash
# Instalar desde requirements actualizado
pip install -r requirements.txt

# Si aún faltan dependencias
pip install PyPDF2 pypdf python-docx streamlit-option-menu streamlit-option-menu

# Inicializar sistema
python setup_streamlit.py --init-only
```

### **⚡ SOLUCIÓN 3: Instalación Completa**

```bash
# Instalar todas las dependencias de una vez
pip install PyPDF2 pypdf python-docx streamlit-option-menu plotly pandas streamlit streamlit-option-menu

# Verificar instalación
python -c "import PyPDF2; print('PyPDF2 instalado correctamente')"

# Ejecutar sistema
python setup_streamlit.py --init-only
```

---

## 🔧 **¿POR QUÉ OCURRE ESTE ERROR?**

### **Causa Técnica:**
1. **Librerías faltantes**: `PyPDF2`, `python-docx`, `streamlit-option-menu`
2. **Version conflict**: Algunas dependencias no se instalaron correctamente
3. **Environment issue**: El entorno virtual no tiene todas las dependencias

### **Archivos Afectados:**
- `src/document_processor.py` → Usa `PyPDF2`
- `app.py` → Usa `streamlit-option-menu`
- Varios archivos → Usan `pandas`, `plotly`

---

## 🛠️ **SOLUCIÓN PASO A PASO DETALLADA**

### **Paso 1: Identificar dependencias faltantes**
```bash
# Verificar qué está instalado
pip list | grep -E "(PDF|docx|streamlit|plotly)"

# Verificar PyPDF2 específicamente
python -c "import PyPDF2; print('PyPDF2 OK')"
```

### **Paso 2: Instalar dependencias**
```bash
# Instalar una por una para identificar problemas
pip install PyPDF2
pip install python-docx  
pip install streamlit-option-menu
pip install plotly
pip install pandas
```

### **Paso 3: Verificar instalación**
```bash
# Probar cada librería
python -c "
import PyPDF2, docx, streamlit_option_menu, plotly, pandas
print('✅ Todas las librerías instaladas correctamente')
"
```

### **Paso 4: Ejecutar sistema**
```bash
python setup_streamlit.py --init-only
```

---

## 🆘 **SI AÚN TIENES PROBLEMAS**

### **Error: "pip not found"**
```bash
# Usar python -m pip en lugar de pip
python -m pip install PyPDF2
```

### **Error: "Permission denied"**
```bash
# Instalar solo para el usuario
pip install --user PyPDF2
```

### **Error: "SSL certificate"**
```bash
# Usar flags adicionales
pip install --trusted-host pypi.org --trusted-host pypi.python.org --trusted-host files.pythonhosted.org PyPDF2
```

### **Error: "No module named 'langchain'"**
```bash
# Instalar todas las dependencias principales
pip install langchain langchain-google-genai langchain-chroma chromadb sentence-transformers
```

---

## 🎯 **VERIFICACIÓN FINAL**

### **Comando de verificación completo:**
```bash
cd tp3/

# Instalar todas las dependencias
pip install PyPDF2 pypdf python-docx streamlit-option-menu plotly pandas streamlit langchain langchain-google-genai langchain-chroma chromadb sentence-transformers

# Verificar el sistema
python setup_streamlit.py --check

# Inicializar sistema
python setup_streamlit.py --init-only

# Ejecutar aplicación
python setup_streamlit.py --run
```

---

## 📝 **ARCHIVOS DE CONFIGURACIÓN**

### **Si necesitas actualizar requirements.txt:**
```txt
# Agregar estas líneas al final del archivo
PyPDF2>=3.0.0
pypdf>=3.0.0  
python-docx>=1.0.0
streamlit-option-menu>=0.3.0
plotly>=5.15.0
pandas>=2.0.0
```

---

## ✅ **RESULTADO ESPERADO**

Después de seguir estos pasos, deberías ver:

```
INFO: ✅ Python 3.12.7
INFO: ✅ Todas las dependencias instaladas
INFO: 🚀 Inicializando sistema RAG...
INFO: ✅ Sistema RAG inicializado correctamente
INFO: 📊 Documentos indexados: 0
INFO: 🧠 Modelo embeddings: intfloat/multilingual-e5-large
INFO: 🤖 Modelo LLM: gemini-1.5-flash
```

---

## 🆘 **¿NECESITAS AYUDA ADICIONAL?**

Si sigues teniendo problemas:

1. **Comando de emergencia**:
   ```bash
   pip install --upgrade pip
   pip install -r requirements.txt --force-reinstall
   ```

2. **Verificar versión de Python**:
   ```bash
   python --version  # Debe ser 3.8+
   ```

3. **Usar entorno virtual limpio**:
   ```bash
   python -m venv nuevo_entorno
   source nuevo_entorno/bin/activate  # Linux/Mac
   # nuevo_entorno\Scripts\activate   # Windows
   pip install -r requirements.txt
   ```

**¡El sistema debería funcionar perfectamente después de estos pasos!** 🎉