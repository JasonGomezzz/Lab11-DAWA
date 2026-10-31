# next-components-styling

Laboratorio 11 de Desarrollo de Aplicaciones Web Avanzado: componentes reutilizables combinando **CSS Modules** y **Tailwind CSS** en Next.js (App Router, TypeScript, Turbopack).

Repositorio: https://github.com/JasonGomezzz/Lab11-DAWA.git

## Requisitos

- Node.js 18.18 o superior
- npm

## Instalación y ejecución

```bash
npm install
npm run dev
```

La demo está en http://localhost:3000/styling

Otros scripts: `npm run build`, `npm run start`, `npm run lint`.

## Estructura

```
src/
├── app/
│   └── styling/page.tsx          # Página que reúne todos los componentes
└── components/
    ├── ui/
    │   ├── Button.tsx            # Tailwind (tamaños) + CSS Module (onda, gradientes, spinner)
    │   ├── Button.module.css
    │   ├── Input.tsx             # Tailwind (estructura) + CSS Module (label flotante, shake)
    │   ├── Input.module.css
    │   └── Badge.tsx             # Solo Tailwind
    └── cards/
        └── Card.tsx              # Solo Tailwind
```

## Componentes

| Componente | Variantes / props | Estilizado |
|---|---|---|
| `Button` | `primary`, `secondary`, `outline`; `sm`, `md`, `lg`; `loading`, `disabled`, `fullWidth` | CSS Modules + Tailwind |
| `Badge` | `success`, `error`, `warning`, `info`, `neutral`; tres tamaños; `rounded` | Tailwind |
| `Card` | `title`, `subtitle`, `image`, `footer`, `hover`, `className` | Tailwind |
| `Input` | `label`, `type`, `error`, `helperText`, `icon`, `required`, `disabled` | CSS Modules + Tailwind |

## Cómo probar

1. Abrir `/styling` y recorrer botones, badges y cards (hover con elevación y zoom de imagen).
2. Pulsar "Click para cargar": muestra el spinner durante 2 s.
3. Mantener pulsado cualquier botón para ver el efecto de onda.
4. En el formulario, escribir un email sin `@` para ver el mensaje de error con animación.

## Desviaciones respecto al enunciado

- `next.config.ts`: la regla de Turbopack generada por `create-next-app` aplicaba el loader de Tailwind a todo `*.css`, lo que convertía los `*.module.css` en CSS global y dejaba `styles.button` como `undefined`. Se limitó a `globals.css`.
- `page.tsx`: `bg-gradient-to-br` pasa a `bg-linear-to-br`, nombre vigente en Tailwind CSS v4.
- `Input.tsx`: se agregó `"use client"` y se quitó el estado `isFocused`, que no se usaba.
- `Card.tsx`: se desactiva la regla `no-img-element` en la imagen, porque la URL es externa.
- Los archivos copiados del documento traían espacios no separables (U+00A0) que rompían el parser de CSS; se reemplazaron por espacios normales.
- Se cambió el título de la aplicación en `layout.tsx`.
