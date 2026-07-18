<div align="center">

# 🏠 Domus Control

**Smart home automation system built in Java (OOP)** — project for *Programação Orientada aos Objetos* @ University of Minho (2025/2026)

![Java](https://img.shields.io/badge/-Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)
![Gradle](https://img.shields.io/badge/-Gradle-02303A?style=for-the-badge&logo=gradle&logoColor=white)

</div>

---

## 📖 About

**Domus Control** is a text-based smart home management application, inspired by platforms like Home Assistant. Users organize one or more houses into rooms, each populated with connected devices, and can control them individually or through **automations**, **schedules**, and **scenarios**.

The project focuses on the application of **Object-Oriented Programming** principles — encapsulation, inheritance, polymorphism, and abstraction — to model a flexible, extensible domotics domain.

---

## ✨ Features

- **Multi-user, multi-house support** — a user can own or have access to multiple houses, holding different roles (`ADMIN` or `USER`) in each
- **Rooms & devices** — organize devices (lamps, speakers, curtains, garage doors, relays, rain/luminosity sensors, and more) into rooms
- **Device-specific behavior** — On/Off devices, measurement devices (sensors), and opening devices each expose only the operations that make sense for their type
- **Automations** — triggered by sensor conditions (e.g. close curtains when it starts raining), automatically reverted when the condition stops holding
- **Schedules** — exact-time schedules (e.g. open the garage door at 08:00) and interval schedules (e.g. keep the living room lights on from 20:00 to 23:00), with automatic reversal at the end of an interval
- **Scenarios** — manually triggered sets of actions (e.g. *Wake Up*, *Leave Home*, *Movie Night*, *Bedtime*)
- **Behavioral analysis** — detects recurring manual usage patterns and suggests new automations/schedules to the user
- **Time simulation** — advance the house's internal clock to test schedules and automations without waiting in real time
- **Statistics & queries** — house with highest energy consumption, top-used devices, rooms with most devices, average consumption per room, user with most admin houses, and more
- **State persistence** — save and load the full application state to/from a file
- **Robust exception handling** — dedicated exception types for domain-specific error cases

---

## 🏗️ Architecture Highlights

- **`DomusControl`** — Facade-style central class managing all houses and users
- **`Casa`** — core unit representing a smart house: users, rooms, devices, automations, scenarios, and its own behavioral analyzer
- **`Dispositivo` hierarchy** — abstract base class specialized into `DispositivoOnOff`, `DispositivoMedicao` (sensors, using an Observer-style pattern to notify the house of value changes), and `DispositivoAbertura` (curtains, garage doors)
- **`Acao` / `AcaoComposta`** — command-style actions (`Ligar`, `Desligar`, `AlterarLuminosidade`, ...), with `AcaoPorFiltro` enabling generic bulk operations over filtered sets of devices via functional interfaces
- **`Condicao`** — split into `CondicaoSensor` and `CondicaoTemporal`, unifying automations and schedules under a single `Automacao` class (`AutomacaoEstado` for toggling conditions, `AutomacaoEvento` for one-shot events)
- **`Analisador`** — detects recurring usage patterns (`Padrao`) and proposes new `AutomacaoEvento` suggestions
- **MVC-inspired UI layer** — `TextUI` (presentation) → `SistemaController` (coordination) → `DomusControl` (domain model)

A full class diagram is included in the project report.

---

## 🚀 Getting Started

The project is built with **Gradle** (wrapper included).

### Build

```bash
./gradlew build
```

### Run

```bash
./gradlew run --console=plain
```

> On Windows, use `gradlew.bat` instead of `./gradlew`.

---

<div align="center">

🔗 [github.com/miguelprcorreia/Domus-Control](https://github.com/miguelprcorreia/Domus-Control)

</div>
