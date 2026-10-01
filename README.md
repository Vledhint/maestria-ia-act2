# maestria-act2-repo · Transformers y LLM sobre Banking77

Actividad individual de **Sistemas Cognitivos Artificiales**: clasificación multiclase de consultas bancarias (PolyAI/banking77, 77 intenciones) con **DistilRoBERTa**, y explicación de los errores del clasificador con **Falcon-7b-instruct** mediante un *prompt* calibrado.

## Contenido

| Ruta | Descripción |
|---|---|
| `SCA_Banking77_Transformers_LLM.ipynb` | Entregable: notebook autoexplicativo (EDA, *fine-tuning*, evaluación, *prompt engineering*, conclusiones y referencias) |
| `tools/build_notebook.py` | Genera el notebook a partir de código versionable |
| `tests/` | Pruebas `pytest` de las funciones auxiliares (se cargan desde la celda `helpers` del notebook) |
| `outputs/` | Predicciones, métricas y resultados del LLM generados al ejecutar el notebook |
| `CHANGELOG.md` | Registro de cambios y aprendizajes |

## Cómo ejecutar

**Google Colab (recomendado para la entrega completa)**
1. Sube el notebook y selecciona *Entorno de ejecución → Cambiar tipo → GPU (T4 o superior)*.
2. *Entorno de ejecución → Ejecutar todas*. En una T4, Falcon-7b se carga en 4 bits de forma automática.
3. Completa las celdas marcadas con ✍️ con tus propias observaciones de la sección 4 y exporta a PDF.

**Local (secciones 1–3 en CPU)**
```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
jupyter nbconvert --to notebook --execute SCA_Banking77_Transformers_LLM.ipynb
```

**Pruebas**
```bash
python -m pytest -q
```

Variables de entorno solo para pruebas rápidas del código: `FAST_DEV_RUN=1` (subconjunto, 1 época), `FORCE_RUN_LLM=1 LLM_MODEL_ID=hf-internal-testing/tiny-random-FalconForCausalLM` (sección 4 sin GPU).
