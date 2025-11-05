# Pruebas de Rendimiento JMeter - FLYR

Este repositorio contiene el plan de pruebas de rendimiento desarrollado en Apache JMeter como parte de la prueba técnica para Test Automation Engineer.

El objetivo es evaluar la carga de la página `https://nuxqa4.avtest.ink/` y simular flujos de usuario bajo carga.

## Requisitos Previos

Para ejecutar estas pruebas, es necesario tener el siguiente software instalado:

1.  **Java 8 (o superior):** JMeter está basado en Java. Puedes verificar tu versión en la terminal con `java -version`.
2.  **Apache JMeter:** Puedes descargarlo desde [jmeter.apache.org](https://jmeter.apache.org/download_jmeter.cgi). Estas pruebas fueron desarrolladas con la versión **[ 5.6.3]**.

## Plugins Requeridos

Este plan de pruebas utiliza componentes que no vienen en la instalación estándar de JMeter. Es necesario instalar los siguientes plugins:

1.  **JMeter Plugins Manager:** Es el instalador de plugins.
    * Descarga el archivo `plugins-manager.jar` desde `jmeter-plugins.org`.
    * Cópialo dentro de la carpeta `lib/ext` de tu instalación de JMeter.
    * Reinicia JMeter.

2.  **Stepping Thread Group:**
    * Una vez reiniciado JMeter, ve a `Options > Plugins Manager`.
    * En la pestaña `Available Plugins`, busca e instala **`jpgc-Stepping Thread Group`**.
    * JMeter se reiniciará de nuevo.

Ahora el plan de pruebas se podrá ejecutar correctamente.

## Configuración del Entorno

1.  Clona este repositorio en tu máquina local:
    ```bash
    git clone [https://github.com/](https://github.com/)[TU_USUARIO_DE_GITHUB]/performance-tests-jmeter.git
    cd performance-tests-jmeter
    ```
2.  Asegúrate de ejecutar los comandos desde la carpeta `bin` de tu instalación de JMeter.

---

## Ejecución de las Pruebas

El plan de pruebas `flyr_test_plan.jmx` (o el nombre que le hayas puesto) contiene los 3 casos de prueba solicitados.

Para ejecutar las pruebas y generar el reporte HTML, **no se debe usar la GUI (interfaz gráfica)**. Los reportes de carga solo son válidos desde la línea de comandos.

Utiliza el siguiente comando en tu terminal, según tu sistema operativo:

###  Instrucciones para macOS / Linux

```bash
# Navega a la carpeta 'bin' de tu instalación de JMeter
# Ejemplo: cd /ruta/a/apache-jmeter-5.6.3/bin

# Ejecuta la prueba (reemplaza las rutas de ejemplo por tus rutas absolutas)
./jmeter.sh -n -t /ruta/a/tu/proyecto/flyr_test_plan.jmx -l /ruta/a/tu/proyecto/log.jtl -e -o /ruta/a/tu/proyecto/results

# -n : Modo Non-GUI (sin interfaz)
# -t : Ruta a tu archivo .jmx
# -l : Ruta donde se guardará el log de resultados (archivo .jtl)
# -e : Generar reporte HTML al finalizar
# -o : Carpeta donde se guardará el reporte HTML (debe estar vacía o no existir)
```
### Instrucciones para Windows (CMD o PowerShell)
```bash
# Navega a la carpeta 'bin' de tu instalación de JMeter
# Ejemplo: cd C:\JMeter\apache-jmeter-5.6.3\bin

# Ejecuta la prueba (reemplaza las rutas de ejemplo por tus rutas absolutas)
jmeter.bat -n -t C:\ruta\a\tu\proyecto\flyr_test_plan.jmx -l C:\ruta\a\tu\proyecto\log.jtl -e -o C:\ruta\a\tu\proyecto\results

# -n : Modo Non-GUI (sin interfaz)
# -t : Ruta a tu archivo .jmx
# -l : Ruta donde se guardará el log de resultados (archivo .jtl)
# -e : Generar reporte HTML al finalizar
# -o : Carpeta donde se guardará el reporte HTML (debe estar vacía o no existir)
```
### Ver Reportes
Una vez finalizada la ejecución, navega a la carpeta results (o la que hayas especificado en el comando -o).
Abre el archivo index.html en tu navegador para ver el dashboard del reporte de rendimiento con todas las métricas solicitadas.
