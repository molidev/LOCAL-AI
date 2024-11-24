# LOCAL-AI 

# ¿Quieres ejecutar una IA en tu ordenador? 😎

Has llegado al lugar adecuado, a continuación tienes una guía para poder configurar y ejecutar una IA en tu ordenador. </br>
Para ello, usaremos herramientas como WSL, Docker, Ollama y Stable Diffusion.

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

- Un ordenador con Windows 10/11 (con soporte para WSL) / sistema operativo Linux nativo / virtualizado (Ubuntu 24.04.1 nativo)
- Una tarjeta gráfica (GPU) compatible con <b>CUDA</b> (opcional para mejor rendimiento).

---

## Configuración Inicial

### 1. Configura WSL (Windows Subsystem for Linux)
⚠️ <ins>***Este paso es sólo para las personas que quieran usar el sistema sin utilizar linux nativo***</ins>
1. Instala WSL y Ubuntu 24.04.1 : </br>

   Nos dirijimos al símbolo del sistema (CMD) o PowerShell para introducir el siguiente comando:
   
   ```bash
   wsl --install
   ```
   Para evitar problemas, es necesario reiniciar el ordenador una vez finalice la instalación
   Una vez instalado introduciremos un nombre de usuario y contraseña (al escribirla, no se verá por pantalla)
   
2. Actualización del sistema ubuntu

   ⚠️ <ins>***Este paso es común para las personas que decidan optar por usar WSL o Linux nativo***</ins>
   
   ```bash
   sudo apt-get upgrade
   ```

   ```bash
   sudo apt-get upgrade
   ```
   Es recomendable tener actualizado el sistema para evitar problemas futuros en los siguientes pasos 😉

## Instalación de Docker

Una forma rápida y sencilla es ejecutar sobre contenedores docker toda lo que necesitamos. </br>
¿<ins>No sabes lo que es docker</ins>? Puedes verlo [aquí.](https://docs.docker.com/get-started/docker-overview/)

### 1. Actualiza los paquetes y agrega la clave GPG de Docker:

```bash
sudo apt-get install ca-certificates curl
```

```bash
sudo install -m 0755 -d /etc/apt/keyrings
```

```bash
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
```

```bash
sudo chmod a+r /etc/apt/keyrings/docker.asc
```
