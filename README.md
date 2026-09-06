# Operador Booleano

Constructor local de URLs de búsqueda de Google con operadores booleanos avanzados.
Un solo archivo HTML: **sin backend, sin frameworks, sin build step, sin dependencias**.

## Uso

- **Local:** descarga el repo y abre `index.html` en el navegador.
- **GitHub Pages:** activa Pages sobre la rama `main` (carpeta raíz) y visita la URL publicada.

## Qué construye

| Campo | Operador generado |
|---|---|
| Palabra clave — *Obligatoria* | `término` (el espacio es AND implícito en Google) |
| Palabra clave — *Alguna* | `(a OR b)` |
| Palabra clave — *Excluir* | `-término` |
| Frase exacta | `"frase exacta"` |
| Formato de archivo | `filetype:pdf` · `(filetype:doc OR filetype:docx)` |
| Sitio o dominio | `site:ejemplo.org` |
| Excluir sitio | `-site:ejemplo.org` |
| Título contiene | `intitle:término` |
| URL contiene | `inurl:término` |
| Rango de fechas | `&tbs=qdr:d|w|m|y` · `&tbs=cdr:1,cd_min:…,cd_max:…` |
| Idioma | `&lr=lang_es` |
| Región | `&cr=countryES` |

La query se muestra en vivo en texto plano y solo se codifica con `encodeURIComponent`
al construir la URL final.

## Detalles de sintaxis que la herramienta respeta

- `OR` debe ir en mayúsculas; en minúsculas Google lo trata como una palabra más.
- `OR` tiene mayor precedencia que el AND implícito, por eso los grupos van entre paréntesis:
  `gato (perro OR loro)` ≠ `gato perro OR loro`.
- El guion de exclusión va **pegado** al término: `-spam`, nunca `- spam`.
- Los términos con espacios se entrecomillan automáticamente para no partirse en varios.

## Estructura

```
.
├── index.html    # la aplicación completa (HTML + CSS + JS embebidos)
├── README.md
├── LICENSE
└── .gitignore
```

## Licencia

MIT — ver [LICENSE](LICENSE).
