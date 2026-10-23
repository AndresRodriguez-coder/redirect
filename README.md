# redirect

Sitio estático que redirige enlaces cortos a las aplicaciones de la empresa que
se publican con una dirección IP. Sirve porque WhatsApp y otras apps toman una
dirección como `134.209.72.183` por un número de teléfono; un enlace con letras
no se confunde.

## Enlaces

| Enlace | Destino |
|---|---|
| `https://<sitio>.onrender.com/gastos/` | `https://134.209.72.183/` (Gastos Externos) |

Compartir siempre el enlace **con la barra final** (`/gastos/`).

## Estructura

```
redirect/
├── index.html          # página neutra (no lista las aplicaciones)
├── README.md
└── gastos/
    └── index.html      # redirige a Gastos Externos
```

## Agregar otra aplicación

1. Copiar la carpeta `gastos/` con el nombre del enlace (por ejemplo `inventario/`).
2. En su `index.html`, cambiar la dirección de destino en los **3 lugares**
   marcados con `DESTINO` y el título de la página.
3. Publicar (ver abajo). El enlace nuevo será `https://<sitio>.onrender.com/inventario/`.

## Cambiar el destino (por ejemplo, si cambia la IP del servidor)

Editar los 3 lugares `DESTINO` de la carpeta de esa aplicación y publicar de
nuevo. Los enlaces ya compartidos siguen funcionando.

## Publicar en Render

1. Subir esta carpeta a un repositorio de GitHub (puede ser privado).
2. En Render: **New → Static Site**, elegir el repositorio.
3. **Build Command:** vacío. **Publish Directory:** `.`
4. Nombre del sitio: `redirect`. Render exige que el subdominio sea único en todo
   Render; si `redirect` está ocupado, le agrega un sufijo y esa será la dirección
   final (ver el nombre que muestra el panel).
5. Probar `https://<sitio>.onrender.com/gastos/` desde un celular.

## Notas

- La redirección se hace con `meta refresh` y JavaScript, no con un código HTTP
  301, para que el navegador no guarde el destino de forma permanente.
- La dirección del servidor aparece solo dentro de los atributos del enlace,
  nunca como texto visible, para que las apps no la conviertan en teléfono.
- Si Render tuviera una caída, el enlace corto no abre, pero la dirección directa
  del servidor sigue funcionando.
