# LOCAL-AI

# ¿Quieres ejecutar una IA en tu ordenador? 😎

Has llegado al lugar adecuado, a continuación tienes una guía para poder configurar y ejecutar una IA en tu ordenador. </br> Para ello, usaremos herramientas como WSL, Docker, Ollama y Stable Diffusion.

---

## ¿Qué vamos a ver? 🔎

🔹 1. [Requisitos Previos](#requisitos-previos) </br>
🔹 2. [Configuración Inicial](#configuración-inicial) </br>
🔹 3. [Instalación de Docker](#instalación-de-docker) </br>
🔹 4. [Configuración de Ollama](#configuración-de-ollama) </br>
🔹 5. [Instalación de Stable Diffusion](#instalación-de-stable-diffusion) </br>
🔹 6. [Ventajas e Inconvenientes](#ventajas-e-inconvenientes) 

---

## Requisitos Previos 💻

- Un ordenador con Windows 10/11 (con soporte para WSL) / sistema operativo Linux nativo / virtualizado (Ubuntu 22.02 nativo)
- Una tarjeta gráfica (GPU) compatible con <b>CUDA</b> (opcional para mejor rendimiento).

---

## Configuración Inicial

### 1. Configura WSL (Windows Subsystem for Linux)
⚠️ <ins>***Este paso es sólo para las personas que quieran usar el sistema sin utilizar linux nativo***</ins>
1. Instala WSL y Ubuntu: </br>
   
   ```bash
   wsl --install
