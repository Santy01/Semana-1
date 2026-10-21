# Planificador Turístico Inteligente de la Zona Centro del Ecuador

Proyecto académico: constructor de itinerarios con mapa que utiliza RAG y un agente de alcance controlado sobre un catálogo verificado de atractivos de **Tungurahua, Chimborazo, Cotopaxi y Bolívar**, con pronóstico del clima de una API externa.

**Estado:** Semana 1 (propuesta, requisitos, arquitectura, fuentes, catálogo inicial y levantamiento). El RAG y el agente **no están implementados**.

## Estructura

```
.
├── README.md
├── .gitignore
├── .env.example
├── requirements.txt
├── docs/
│   ├── 01-propuesta.md
│   ├── 02-requisitos.md
│   ├── 03-arquitectura.md
│   ├── 04-fuentes.md
│   ├── levantamiento.md
│   └── evidencias/
│       └── semana-1/
│           └── README.md
├── data/
│   ├── raw/                  # documentos fuente descargados (no versionados)
│   └── catalogo/
│       ├── atractivos.csv
│       └── README.md
├── src/
│   └── main.py               # esqueleto FastAPI con /health
└── tests/
```

## Instalación

Requisitos: Python 3.10 o superior.

```bash
# 1. Crear y activar entorno virtual
python -m venv .venv
# Windows (PowerShell)
.venv\Scripts\Activate.ps1
# Linux / macOS
source .venv/bin/activate

# 2. Instalar dependencias
pip install -r requirements.txt

# 3. Configurar variables de entorno
cp .env.example .env        # en PowerShell: Copy-Item .env.example .env
# Edite .env y complete los valores. Nunca suba .env al repositorio.

# 4. Ejecutar el servidor
uvicorn src.main:app --reload
```

Verificar: abrir `http://127.0.0.1:8000/health`, debe responder `{"status": "ok"}`.

## Variables de entorno

Ver `.env.example`. Las claves reales no se versionan.

## Datos

- `data/catalogo/atractivos.csv` contiene 45 atractivos. Costos y coordenadas están marcados `POR VERIFICAR` y deben completarse con fuentes oficiales. Ver `data/catalogo/README.md`.
- `data/raw/` almacena los documentos descargados; está excluido de Git.

## Documentación

1. [Propuesta](docs/01-propuesta.md)
2. [Requisitos](docs/02-requisitos.md)
3. [Arquitectura](docs/03-arquitectura.md)
4. [Fuentes](docs/04-fuentes.md)
5. [Levantamiento](docs/levantamiento.md)
6. [Evidencias de la Semana 1](docs/evidencias/semana-1/README.md)

## Aviso

La información turística debe contrastarse con fuentes oficiales. El sistema no realiza reservas ni pagos ni emite recomendaciones médicas o de seguridad.
