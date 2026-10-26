# text2sql-agent

Agente que te permite interactuar con cualquier base de datos en lenguaje natural

## 🎥 Vídeo del tutorial

[![Ver el tutorial](https://img.youtube.com/vi/6CILJuWKVBE/maxresdefault.jpg)](https://youtu.be/6CILJuWKVBE)

▶️ [Ver el tutorial en vídeo](https://youtu.be/6CILJuWKVBE)

## Descripción

En esta demo de nivel intermedio verás un caso de uso muy común y muy útil para equipos de software, y sobre todo para los departamentos no técnicos: un agente que te permite interactuar con cualquier base de datos en lenguaje natural. Una versión simple (y gratuita) de [askyourdatabase.com](http://askyourdatabase.com/).

Yona, experto en IA, te mostrará en detalle:

- La lógica para construir la query SQL a partir de lenguaje natural, según la consulta del usuario y conocida la estructura de la base de datos.
- La lógica para ejecutar la query en la base de datos.
- La lógica y el diseño de la respuesta en lenguaje natural para interactuar a través de una interfaz tipo ChatGPT de manera completamente conversacional.

Aprenderás:

- ✅ A integrar fuentes de datos externas.
- ✅ A construir agentes con Python y LangChain.
- ✅ A construir interfaces conversacionales con Chainlit.


## Estructura de carpetas

```plaintext
📦 webinar_text2sql
├── 📁 chatbot                                          # Código Text-to-SQL 
│   ├── 📄 __init__.py                                  # Convierte un directorio en un paquete
│   ├── 📄 chatclass.py                                 # Clase del agente text2sql 
│   └── 📄 prompts.py                                   # Prompts del sistema
│
├── 📁 images                                           # Carpeta con las imagenes usadas
│
├── 📁 notebooks                                        # Carpeta de notebooks de prueba
│   ├── 📁 src                                          # Carpeta de codigo del chat
│   │   └── 📄 chat.py                                  # Función del chatbot
│   ├── 📄 Consultor SQL OpenAI y Langchain.ipynb       # Jupyter notebook con el paso a paso
│   └── 📄 practicas.ipynb                              # Jupyter notebook con 10 preguntas de prueba
│
├── 📁 sakila_db                                        # Carpeta con el archivo de la base de datos
│   └── 📄 sakila.sql                                   # Archivo autocontenido de la base de datos
│
├── 📁 tools                                            # Herramientas 
│   ├── 📄 __init__.py                                  # Convierte un directorio en un paquete
│   └── 📄 tools.py                                     # Herramientas (logger)
│
├── 📄 .env.template                                    # Plantilla de archivo .env 
├── 📄 .gitignore                                       # Archivos y carpetas a ignorar en Git
├── 📄 .python-version                                  # Versión de python
├── 📄 front.py                                         # Archivo del frontend con chainlit
├── 📄 pyproject.toml                                   # Dependencias y configuración 
├── 📄 README.md                                        # Documentación principal del proyecto
├── 📄 requirements.txt                                 # Dependencias y configuración 
└── 📄 uv.lock                                          # Dependencias y configuración 
```

## Estructura de la base de datos
Usaremos la base de datos [sakila](https://dev.mysql.com/doc/sakila/en/sakila-installation.html), una base de datos de ejemplo que podemos descargar desde [aquí](https://github.com/YonatanRA/webinar_text2sql/raw/refs/heads/main/sakila_db/sakila.sql). Sus características son las siguientes:

+ Dominio del negocio: Videoclub (alquiler de películas).

+ Tamaño: Mediana complejidad, ideal para practicar consultas SQL reales.

+ Relaciones: Incluye múltiples relaciones entre tablas, ideal para practicar joins, subqueries, views y stored procedures.

+ Diagrama entidad-relación:
![erd](https://raw.githubusercontent.com/YonatanRA/webinar_text2sql/refs/heads/main/images/erd.png)



## Dependencias

1. **Instalación `uv`**:

   El método de instalación recomendado de `uv` es:

   ```bash
   curl -LsSf https://astral.sh/uv/install.sh | sh
   ```

   De manera alternativa, podemos instalar `uv` via `pip`:

   ```bash
   pip install uv
   ```

   Para más detalles, revisar los [métodos de instalación](https://docs.astral.sh/uv/getting-started/installation/#installation-methods).



2. **Activación del entorno virtual**

    Activar el entorno virtual usado el siguiente comando:

    ```bash
    source .venv/bin/activate
    ```

    También puede usarse conda y crear un entorno virtual con:
     ```bash
    conda create -n sql python=3.11
    ```

3. **Sincronizar dependencias con uv**:

    ```bash
    uv sync
    ```

    Este comando instala las dependencias definidas en el archivo `pyproject.toml` con las mismas versiones especificadas en el archivo `uv.lock`.

4. **Sincronizar dependencias con pip**:

    ```bash
    pip install -r requirements.txt
    ```

    Este comando instala las dependencias en el entorno virtual definidas en el archivo `requirements.txt`. 

## Variables de entorno

Este proyecto necesita de una base de datos SQL (MySQL, PostGres, SQLServer). La URI debe estar escrita en el archivo `.env`. En la platilla de archivo `.env.template` existe un ejemplo de URI para MySQL. Se recomienda usar un usuario con permisos restringidos por seguridad. Se necesita obtener una API KEY de OpenAI [aqui](https://platform.openai.com/api-keys).

`URI = 'mysql+pymysql://user:password@localhost:3306/sakila'`

`OPENAI_API_KEY = 'sk-WrrN..................'`




## Proceso de instalación y uso

1. Crear la base de datos de MySQL sakila. Puede hacerse desde [Workbench](https://www.mysql.com/products/workbench/):
   ![workbench](https://raw.githubusercontent.com/YonatanRA/webinar_text2sql/refs/heads/main/images/import_db.png)

   O también desde la terminal de sql con los siguientes comandos:
   ```bash
    mysql -u root -p 
    ```

    ```bash
    mysql -u root -p sakila < sakila_sql/sakila.sql
    ```

2. Obtener URI de la base de datos de SQL y colocarla en el archivo `.env` (ejemplo en el archivo `.env.template`).


3. Instalar dependencias. Se puede usar el archivo `uv.lock` con el siguiente comando:
    ```bash
    uv sync
    ```
    También puede usarse el archivo `requirements.txt` usando el siguiente comando:
    ```bash
    pip install -r requirements.txt
    ```


4. Levantar el front de chainlit con el siguiente comando:
    ```bash
    chainlit run front.py -w --port 8001
    ```

---

## Copyright

Copyright (c) 2026 LIDR.co. Licensed under the MIT License.

**English:**
The content of this repository is part of the AI Engineering program by LIDR.co. If you want to learn AI Engineering with the pros and get more templates and resources like these, you can find all the information on the official website: https://lidr.co/ai-engineering

**Español:**
El contenido de este repositorio es parte del programa AI Engineering de LIDR.co. Si quieres aprender AI Engineering con los pros, y obtener más plantillas y recursos como estos, puedes encontrar toda la información en la página oficial: https://lidr.co/ai-engineering
