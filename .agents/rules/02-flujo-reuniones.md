# Regla 02: Flujo Obligatorio al Procesar una Reunión

Cuando el usuario pida procesar, registrar o resumir una reunión:

1. **Gestión de Archivos Multimedia:**
   - **NUNCA** subir archivos de audio o video (`.ogg`, `.mp3`, `.mp4`, `.wav`) a Git. Deben estar bloqueados en `.gitignore`.
   - Si existen audios, subirlos a Google Drive / OneDrive y registrar el link público en el acta.

2. **Estructura de Carpeta:**
   - Crear subdirectorio `docs/reuniones/YYYY-MM-DD_<nombre_descriptivo>/` (ej. `docs/reuniones/2026-09-08_reu1/`).

3. **Transcripción (`transcripcion.md`):**
   - Limpiar muletillas excesivas manteniendo la fidelidad técnica.
   - Organizar por turnos de orador con marcas de tiempo (`[MM:SS]`).
   - Añadir resumen de secciones temáticas al inicio.

4. **Acta Formal (`acta.md`):**
   - Usar obligatoriamente la estructura de `docs/reuniones/plantilla_acta.md`.
   - Secciones requeridas: Encabezado (fecha, duración, asistentes, audio externo), Objetivo, Temas tratados, Decisiones tomadas (tabla), Próximos pasos (checklist con responsables).

5. **Actualización de Índices:**
   - Agregar la nueva reunión a la tabla de `docs/reuniones/README.md`.

6. **Impacto en Requerimientos y Decisiones Pendientes:**
   - Si la reunión cambia el alcance o agrega módulos:
     - Cambio mayor: generar nueva versión `docs/requerimientos/v(N+1)/SRS_Fase_X_v(N+1).0.md` y archivar previa.
     - Cambio menor: incrementar versión menor del SRS vigente (ej. v2.1 -> v2.2) y registrar el diff en "Control de Versiones".
   - Actualizar la sección de *Decisiones Pendientes* del SRS vigente (marcar resueltas o añadir nuevas).
