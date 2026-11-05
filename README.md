# `moviles-pcalificada3-leyva`

**Evaluación 03** — Programación en Móviles Avanzado · TECSUP · Ciclo V · 2026-II

[![Repo](https://img.shields.io/badge/GitHub-repo-181717?logo=github&logoColor=white)](https://github.com/johnleyva28/moviles-pcalificada3-leyva) [![Swift](https://img.shields.io/badge/Swift-5.0-339933?logo=swift&logoColor=white)](https://swift.org) [![SwiftUI](https://img.shields.io/badge/SwiftUI-iOS%2026-0f9dbf?logo=swift&logoColor=white)](https://developer.apple.com/swiftui/) [![License](https://img.shields.io/badge/License-Academic-blue)](#-licencia)

---

## 📋 Sobre este repositorio

Este repositorio contiene la solución completa de la **Evaluación 03** del curso *Programación en Móviles Avanzado* de TECSUP. La evaluación propone **cuatro aplicaciones** y se opta por la **opción 4: una app del torneo de Wimbledon (tenis)**. Consta de **cinco pantallas** que suman 20 puntos, cada una con su pregunta analítica.

| # | Pantalla            | Tema                                          | Puntaje | Carpeta                    |
|---|---------------------|-----------------------------------------------|--------:|----------------------------|
| 1 | Splash              | Bienvenida con animación y navegación automática | 4 pts  | [`Splash/`](./moviles-pcalificada3-leyva/Splash) |
| 2 | Login               | Validación de formulario en el ViewModel       | 4 pts  | [`Login/`](./moviles-pcalificada3-leyva/Login) |
| 3 | Registro            | Alta de usuario en memoria con email único    | 4 pts  | [`Registro/`](./moviles-pcalificada3-leyva/Registro) |
| 4 | Home — Listado      | Listado con búsqueda reactiva y logout         | 4 pts  | [`Home/`](./moviles-pcalificada3-leyva/Home) |
| 5 | Detalle del elemento| Navegación con modelo y layout editorial       | 4 pts  | [`Detalle/`](./moviles-pcalificada3-leyva/Detalle) |

---

## 👤 Autor

- **John Marco Leyva Nuñez** — `john.leyva@tecsup.edu.pe`

**Carrera:** Diseño y Desarrollo de Software · **Ciclo:** V · **Grupo:** 01 · **Periodo:** 2026-II

**Docente:** Jorge Enrique Ventura Gonzales

---

## 🛠️ Stack tecnológico

- **SwiftUI** — interfaz declarativa con `NavigationStack`, `ScrollView` + `LazyVStack`, `TabView` y `navigationDestination`
- **Swift 5.0** con *approachable concurrency* y `SWIFT_DEFAULT_ACTOR_ISOLATION = MainActor`
- **Combine / ObservableObject** — estado reactivo con `@Published` y `@StateObject`
- **Xcode 26** — target iOS 26.0, catálogo de assets con vectoriales SVG
- **Photos reales** de los tenistas desde Wikimedia Commons, recortadas a avatares cuadrados

---

## 📂 Estructura del repositorio

```
moviles-pcalificada3-leyva/
├── README.md                              ← este archivo
├── .gitignore
│
└── moviles-pcalificada3-leyva/            ← target de la app
    ├── moviles_pcalificada3_leyvaApp.swift (entry point + SessionStore como @EnvironmentObject)
    ├── ContentView.swift                  (router: Splash → Login → Registro → MainTabView)
    ├── SessionStore.swift                  (usuarios registrados + currentUser)
    ├── WimbledonTheme.swift                (tokens de color, tipografía, radios y espaciado)
    ├── Toast.swift                         (toast reutilizable de error y éxito)
    │
    ├── Splash/
    │   └── SplashView.swift                (escudo oficial + entrada animada + salto a los 2 s)
    ├── Login/
    │   ├── LoginView.swift                 (formulario con SecureField y botón deshabilitado)
    │   └── LoginViewModel.swift            (validación de email y contraseña)
    ├── Registro/
    │   ├── RegistroView.swift              (alta de cuenta con confirmación)
    │   └── RegistroViewModel.swift         (campos vacíos, email único, contraseñas iguales)
    ├── Home/
    │   ├── HomeView.swift                  (banda de estadísticas + lista + búsqueda)
    │   ├── HomeViewModel.swift             (items @Published + filtrado reactivo)
    │   └── ItemModel.swift                 (struct Identifiable)
    ├── Detalle/
    │   └── DetalleView.swift               (hero + lista de definición en ScrollView)
    ├── Perfil/
    │   └── PerfilView.swift                (datos de sesión + cerrar sesión)
    │
    └── Assets.xcassets/
        ├── LogoWimbledon.imageset          (escudo oficial en SVG)
        ├── Jugador*.imageset               (10 avatares de tenistas)
        ├── AccentColor.colorset            (morado de marca)
        └── AppIcon.appiconset              (icono 1024×1024 con el escudo)
```

---

## ⚡ Quick start

### Requisitos

- macOS con **Xcode 16 o superior**
- iOS Simulator (iOS 26.0 o superior)

### Pasos

```bash
git clone https://github.com/johnleyva28/moviles-pcalificada3-leyva.git
cd moviles-pcalificada3-leyva
open moviles-pcalificada3-leyva.xcodeproj
```

1. Seleccionar un **iPhone Simulator** como destino.
2. Presionar **⌘R** para compilar y ejecutar.

No hay dependencias externas: no se usa Swift Package Manager ni CocoaPods. Todo el estado vive en memoria durante la sesión.

### Probar la app

| Pantalla   | Cómo llegar                                                        |
|------------|--------------------------------------------------------------------|
| Splash     | Se muestra al abrir la app y salta al Login a los 2 segundos        |
| Login      | Correo con formato válido y contraseña de 6+ caracteres, 1 mayúscula y 1 carácter especial (no puede ser `.`, `,` ni `;`) |
| Registro   | Nombre, correo, contraseña y su confirmación; el correo debe ser único |
| Home       | Lista de 10 tenistas con búsqueda por nombre, país o mano; cerrar sesión desde **Perfil** |
| Detalle    | Tocar cualquier fila de la lista                                    |

> El ícono de ojo en los campos de contraseña alterna entre texto visible y oculto.

---

## 🎨 Identidad visual

La paleta y el logotipo se extrajeron de los estilos oficiales de **wimbledon.com** (variables CSS `--wdl-*`), no se eligieron al azar.

| Color             | Hex       | Uso                                        |
|-------------------|-----------|--------------------------------------------|
| Morado de marca   | `#54008B` | Escudo, títulos editoriales, tab bar       |
| Morado profundo   | `#240330` | Fondos oscuros, degradados                  |
| Verde de marca    | `#046633` | Botones principales, acentos de texto       |
| Verde de cancha   | `#11742F` | Degradados de fondo                          |
| Verde césped      | `#0E6027` | Avatares                                    |
| Menta             | `#D3F0E0` | Fondo de las listas y el detalle            |
| Lime              | `#F3FF00` | Textos destacados sobre fondo oscuro        |

**Tipografía.** Wimbledon usa Gotham (sans) y Adobe Caslon Pro (serif). Ninguna es licenciable para iOS, así que se mapearon a las fuentes del sistema: SF Pro para etiquetas, botones y datos, y New York (`.serif`) para títulos editoriales y nombres propios. La escala sigue un ratio de 1.25 en 6 pasos (`caption` 11 · `footnote` 13 · `body` 15 · `subhead` 17 · `title` 21 · `display` 28).

**Espaciado y radios.** Dos radios (10 para controles, 16 para contenedores) y un ritmo fijo de 4 / 8 / 12 / 20 / 32.

---

## 📸 Créditos de imágenes

**Escudo de Wimbledon** (`LogoWimbledon.imageset`): tomado de `https://www.wimbledon.com/_next/static/media/Logo-Wimbledon.2wyelfplbl7j4.svg`, sin modificaciones y con sus colores originales (morado `#54008b`, verde `#063` y blanco). Logotipo de Wimbledon © The All England Lawn Tennis and Croquet Club. Se usa con fines académicos, sin implicar afiliación oficial con el torneo.

**Fotografías de los tenistas** (`Jugador*.imageset`): provenientes de Wikimedia Commons y recortadas a 512×512 px. Las licencias CC BY-SA requieren conservar la atribución y compartir las modificaciones bajo la misma licencia.

| Jugador         | Autor                                  | Licencia       | Archivo original                                                                                              |
|-----------------|----------------------------------------|----------------|--------------------------------------------------------------------------------------------------------------|
| Carlos Alcaraz  | Barcex                                 | CC BY-SA 4.0   | [25th Laureus World Sports Awards - Carlos Alcaraz](https://commons.wikimedia.org/wiki/File:25th_Laureus_World_Sports_Awards_-_Red_Carpet_-_Carlos_Alcaraz_-_240422_192324_%28cropped%29.jpg) |
| Jannik Sinner   | The White House                        | Dominio público | [Jannik Sinner 2025 US Open](https://commons.wikimedia.org/wiki/File:Jannik_Sinner_2025_US_Open.jpg) |
| Novak Djokovic  | Andymiah                               | CC BY-SA 4.0   | [Novak Djokovic Paris 2024 Olympic Games](https://commons.wikimedia.org/wiki/File:Novak_Djokovic_Paris_2024_Olympic_Games_%28cropped%29.jpg) |
| Iga Świątek      | Hameltion                              | CC BY-SA 4.0   | [Iga Swiatek 2023 Cropped + Retouched](https://commons.wikimedia.org/wiki/File:Iga_Swiatek_2023_Cropped_%2B_Retouched.jpg) |
| Aryna Sabalenka | Rick Munroe                            | CC BY-SA 4.0   | [Aryna Sabalenka Miami Open Final](https://commons.wikimedia.org/wiki/File:Aryna_Sabalenka_Miami_Open_Final.jpg) |
| Coco Gauff       | Rick Munroe                            | CC BY-SA 4.0   | [Coco Gauff Miami Open](https://commons.wikimedia.org/wiki/File:Coco_Gauff_Miami_Open.jpg) |
| Alexander Zverev| Rick Munroe                            | CC BY-SA 4.0   | [Alexander Zverev in Miami](https://commons.wikimedia.org/wiki/File:Alexander_Zverev_in_Miami.jpg) |
| Jasmine Paolini | Hameltion (original), Blackcat (derivado) | CC BY-SA 4.0 | [Jasmine Paolini (2023 US Open) 01](https://commons.wikimedia.org/wiki/File:Jasmine_Paolini_%282023_US_Open%29_01_%28cropped%29.jpg) |
| Andrey Rublev   | Hameltion                              | CC BY-SA 4.0   | [Andrey Rublev (2023 US Open) 02](https://commons.wikimedia.org/wiki/File:Andrey_Rublev_%282023_US_Open%29_02_%28cropped%29.jpg) |
| Mirra Andreeva  | si.robi                                | CC BY-SA 2.0   | [Mirra Andreeva WMQ23](https://commons.wikimedia.org/wiki/File:Mirra_Andreeva_WMQ23_%28cropped%29.jpg) |

---

## 🪪 Licencia

Material académico del curso *Programación en Móviles Avanzado* de TECSUP. Uso educativo.
