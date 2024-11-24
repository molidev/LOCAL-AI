# LOCAL-AI 

# ¿Quieres ejecutar una IA en tu ordenador? 😎

Has llegado al lugar adecuado, ármate de paciencia que ya comenzamos! A continuación tienes una guía para poder configurar y ejecutar una IA en tu ordenador. </br>
Para ello, usaremos herramientas como <b>WSL, Docker, Ollama y Stable Diffusion</b>.

Esta guía se encuentra en continua actualización, por lo que irá evolucionando. Se agradece cualquier consejo, recomendación y si dejais una ``star`` se agradece </br>
![image](https://github.com/user-attachments/assets/21dc7c96-eb83-4b8b-88c5-46a92c30a572)


---

## ¿Qué vamos a ver? 🔎

🔹 1. [Requisitos Previos](#requisitos-previos-) </br>
🔹 2. [Configuración Inicial](#configuración-inicial) </br>
🔹 3. [Instalación de Ollama](#instalación-de-ollama) </br>
🔹 4. [Instalación de Docker](#instalación-de-docker) </br>
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
   Para evitar problemas, es necesario <b>reiniciar el ordenador</b> una vez finalice la instalación.
   Una vez reiniciado accederemos de nuevo a ubuntu con:
   
   ```bash
   wsl -d Ubuntu
   ```
   
   Una vez instalado introduciremos un nombre de usuario y contraseña (al escribirla, no se verá por pantalla)
   
3. Actualización del sistema ubuntu

   ⚠️ <ins>***Este paso es común para las personas que decidan optar por usar WSL o Linux nativo***</ins>
   
   ```bash
   sudo apt-get upgrade
   ```

   ```bash
   sudo apt-get upgrade
   ```
   Es recomendable tener actualizado el sistema para evitar problemas futuros en los siguientes pasos 😉

## Instalación de OLLAMA
Cuando hemos terminado la configuración inicial ya podemos proceder a instalar [OLLAMA](https://ollama.com/) (herramienta para ejecutar localmente modelos de redes neuronales)
Gracias a esta herramienta podemos utilizar distintos [modelos](https://ollama.com/search), nosotros utilizaremos para probar [llama3.2](https://ollama.com/library/llama3.2)

Procedemos a instalarla con el siguiente comando, el cuál podemos ver en la página oficial de Ollama:
````bash
curl -fsSL https://ollama.com/install.sh | sh
````
Para comprobar que la instalación se ha realizado correctamente, nos dirijimos a un navegador web (Chrome, Firefox, Opera..) y accedemos a la siguiente dirección: 
[localhost:11434](http://localhost:11434) en ella debe aparecernos un mensaje que pondrá: <ins>"Ollama is running"</ins>

![image](https://github.com/user-attachments/assets/5816a9a5-1624-4c6d-97f5-a919cd5d9b88)

Ahora vamos a proceder a descargar el modelo [llama3.2](https://ollama.com/library/llama3.2), en la terminal, escribiremos el siguiente comando:
```bash
ollama pull llama3.2
````
Ya va siendo hora de probar, no? 😜 Para poder hacer una primera prueba desde la terminal, escribimos el comando: 

```bash
ollama run llama3.2
```
Esto funciona... pero nosotros queremos una interfaz tipo <b>ChatGPT</b> que sea más fácil de gestionar.</br> Por ello, procederemos con los siguientes pasos donde utilizaremos [open-webui](https://openwebui.com/) 🔎

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
Añadiremos la nueva source y actualizaremos
```bash
echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
$(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```
### 2. Instalación de componentes + docker

Instalamos docker para poder ejecutar open-webui 😎
```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
Lanzamos el contenedor con [open-webui](https://openwebui.com/), es decir, controlaremos absolutamente todo desde una interfaz muy sencilla. No sólo, podemos usar el modelo Llama3.2 sino los que queramos a la vez, como iremos viendo.</br>
⚠️ <ins>***Si observamos el comando, le estamos indicando la url donde tenemos funcionando previamente OLLAMA***</ins>

```bash
sudo docker run -d --network=host -v open-webui:/app/backend/data -e OLLAMA_BASE_URL=http://127.0.0.1:11434 --name open-webui --restart always ghcr.io/open-webui/open-webui:main
```
Mediante el comando ``sudo docker ps`` podemos ver que está en funcionamiento:

![image](https://github.com/user-attachments/assets/e426cc57-8a07-44ce-b6bc-1d18baa0fcdf)

Y si has llegado hasta aquí, ahora sí, puedes ir al a tu navegador web y poner la dirección: [localhost:8080](http:\\localhost:8080) aquí: 

Crearemos una cuenta y ya podremos disfrutar de "correr" nuestro propio modelo de IA en nuestro PC con toda la privacidad que ello conlleva:

![image](https://github.com/user-attachments/assets/cb2a9349-df73-44ab-91a8-9450726220c0)

<ins>En la imagen salen otros modelos que debido a las pruebas realizado ya he instalado</ins>

### 3. Instalar más modelos + configuración

Nos dirijimos a esta sección : ``Panel de administración``

Aquí debemos tener la siguiente configuración, en la que le indicamos la BASE_URL de OLLAMA:

![image](https://github.com/user-attachments/assets/25253fdb-508b-46ad-bb12-213e4a798826)

Para instalar más modelos únicamente basta con ir a [modelos](https://ollama.com/search) y seleccionar el que mejor se adapte a nuestra máquina.
Lo puedes ver de forma más gráfica aquí, hay que fijarse en el nombre exacto para que pueda ser instalado:

![image](https://github.com/user-attachments/assets/5b5a41ee-4a38-48ae-a03a-0115fd1f487e)

Selecciona el modelo en un nuevo chat y a disfrutar:

![image](https://github.com/user-attachments/assets/c299cf5c-c259-48d7-a4e9-74cbc6266578)

⚠️ <ins>***Recuerda que cuanto más sea pesado(más parámetros admita) el modelo, será más completo pero tienes que tener en cuenta los requisitos de tu máquina</ins>***


## Ventajas e Inconvenientes

Una vez que he probado con totalidad el sistemas, te dejo por aquí tienes una tabla resumen con algunas ventajas e inconvenientes para tener en cuenta, para mi la principal ventaja que tiene es la privacidad que tiene respecto a servicios contratados:

| Ventajas                                                | Inconvenientes                                           |
|---------------------------------------------------------|---------------------------------------------------------|
| Control total sobre la configuración de tu IA.          | Requiere conocimientos técnicos avanzados.              |
| No dependes de servicios en la nube.                    | Puede consumir muchos recursos del sistema.             |
| Personalización según tus necesidades.                  | Configuración inicial puede ser compleja y lenta.       |
| Ahorro en costes de uso de servicios externos.          | No es viable sin hardware compatible (GPU potente).     |




