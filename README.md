# Horse Swing

Java Swing desktop application that presents a four-horse race simulation with animated race lanes and a start/restart control.

![Java 11](https://img.shields.io/badge/Java-11-007396?style=flat-square)
![Swing](https://img.shields.io/badge/UI-Swing-2F6DB0?style=flat-square)
![Desktop application](https://img.shields.io/badge/Category-Desktop%20application-555555?style=flat-square)
![Academic project](https://img.shields.io/badge/Classification-Academic%20project-CB8A00?style=flat-square)
![Year | 2023](https://img.shields.io/badge/Year%20%7C%202023-6B7280?style=flat-square)

> [!NOTE]
> This repository contains an academic project originally developed during earlier programming studies. It is preserved as a record of the technical knowledge, design decisions, and development experience acquired at the time.

## Overview

Cavalli Swing builds a desktop race view with four horse lanes. Pressing the **Gioca** button creates a race manager and starts one worker thread per horse. Each horse advances by a configured increment after a randomized delay; when a horse reaches the configured finish position, the race manager stops the workers.

The user interface observes changes to each horse's position and updates the corresponding Swing label. The application includes the horse images, logo, and track image required by the view.

## Features

- Starts or restarts a race from the Swing interface.
- Simulates four independently advancing horses using Java threads.
- Updates horse positions through model listeners.
- Stops the race when a horse reaches the configured finish position.
- Uses bundled image assets for the application icon, horses, and track.

## Technology stack

- **Language:** Java
- **UI toolkit:** Java Swing
- **Runtime/compiler target:** Java 11
- **Project tooling:** Eclipse Java project metadata

The repository has no dependency manifest or external library declaration; the source uses Java and Swing APIs.

## Architecture

The source follows an educational separation of responsibilities:

- `bean` contains `Cavallo` and `Gioco`, which hold race state.
- `business` contains `Fantino`, `GestoreGioco`, and `GestorePulsante`, which coordinate worker threads and button actions.
- `interfaces` contains the `CavalloModificato` listener contract.
- `views` contains the Swing frame and race-lane components.
- `main` contains the `Main` entry point and the singleton `Config` object.

This is a practical package-level separation rather than a formally documented production architecture.

## Project structure

```text
Cavalli Swing/
├── src/it/volta/ts/ulivisamuel/cavalli_swing/
│   ├── bean/
│   ├── business/
│   ├── interfaces/
│   ├── main/
│   └── views/
├── img/
│   ├── cavalloN1.png
│   ├── cavalloN2.png
│   ├── cavalloN3.png
│   ├── cavalloN4.png
│   ├── logo.jpg
│   └── track.png
├── .classpath
├── .project
└── .settings/
```

## Getting started

### Prerequisites

- JDK 11.
- Eclipse or another Java IDE capable of importing an Eclipse Java project.

The required Java level is declared in `.classpath` and `.settings/org.eclipse.jdt.core.prefs`.

### Import and run with Eclipse

1. Import the `Cavalli Swing` directory as an existing Eclipse project.
2. Run `it.volta.ts.ulivisamuel.cavalli_swing.main.Main` as a Java application.
3. In the application window, press **Gioca** to start or restart the race.

The source loads image assets using relative paths under `img/`; keep the project working directory aligned with the `Cavalli Swing` directory when launching the application.

### Compile from a terminal

From the repository root:

```bash
cd "Cavalli Swing"
mkdir -p bin
find src -name '*.java' -print0 | xargs -0 javac -d bin
```

The command compiles the repository's Java sources into the Eclipse-configured `bin` output directory. The application entry point is:

```text
it.volta.ts.ulivisamuel.cavalli_swing.main.Main
```

## Testing

No automated test sources or test configuration are present in the repository. Compilation is the available verification step.

## Project status

The Git history records the original implementation as completed in March 2023. The repository is retained as an academic project rather than documented as a current production application.

## License

This project is shared for educational and portfolio purposes. All rights reserved unless otherwise stated.
