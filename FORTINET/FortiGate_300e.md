<img src="../STATIC/images/logo.png" align="center" width="200px"></img>
<h1 align="center">Configuración de FORTIGATE 300E (FORTINET)</h1>

> [!NOTE]
>Aquí encontrarás los pasos y/o accesorios que se requiere para una buena validación de este modelo de equipo, ten en cuenta que esta información es basico para poder realizar la validación solicitado por el Cliente


## Accesorio usadas
| Accesorio           |Descripción                                                                      |
|---------------------|---------------------------------------------------------------------------------|
| `Cable consola`       | Conexión entre el adaptador DB9 y el puerto consola del equipo. |
| `Adaptador USB  DB9`  | Adaptador de usb hacia el cable consola, necesaria para conexión del cable consola y el computador   |
| `Patch Cord RJ45 568B`| Conector entre los puertos RJ45 del equipo y el computador     |

## Diagrama de conexión

## Pasos para interacción con la CLI [PuTTY](https://www.putty.org/)
> [!TIP]
>Validar el numero del puerto COM al que esta conectado el cable serial en el "administrador de dispositivo" del computador

1. Iniciar el programa PuTTY una vez conectado el equipo(Router) al computador.

2. En la ventana de PuTTY, en la sección de configuración de la conexión, selecciona la conexión serie (Serial) en el panel izquierdo.

3. En la configuración de la conexión serie, ingresa COM# en el campo que indica "Serial line to connect to" o "Puerto serie a conectar".

4. Configura la velocidad (Speed) con valor de 9600 que viene por defecto en algunos casos, iniciar con el boton Open.

5. Se abrirá una ventana de terminal. En ella, deberás iniciar sesión con las credenciales del dispositivo FortiGate (nombre de usuario y password).

6. Ingresa el nombre de usuario por defecto `admin` cuando se te solicite y presiona Enter. Luego, se te pedirá que ingreses la contraseña por defecto " ". Ten en cuenta que mientras escribes la contraseña, no verás ningún indicador visual (ni asteriscos ni caracteres), pero aún así se está registrando lo que escribes. Presiona Enter después de ingresar la contraseña.

```
FortiGate-300E login: admin
Password: *****
Welcome !
```


 

## Comandos para extraer información

1. **Información del dispositivo**

```
get system status
```
- se utiliza para obtener una visión general del estado del sistema en tiempo real. Este comando proporciona información esencial sobre el dispositivo:

    - Versión del firmware
    - Uso de la CPU
    - Uso de la memoria
    - Información de la tarjeta de red
    - Números de serie y otros detalles del hardware:

```
FortiGate-300E # get system status
Version: ******************************
Virus-DB: 90.04713(2022-08-02 15:20)
Extended DB: 90.04713(2022-08-02 15:19)
Extreme DB: 1.00000(2018-04-09 18:07)
IPS-DB: 6.00741(2015-12-01 02:30)
IPS-ETDB: 6.00741(2015-12-01 02:30)
APP-DB: 6.00741(2015-12-01 02:30)
INDUSTRIAL-DB: 6.00741(2015-12-01 02:30)
Serial-Number: ***************
IPS Malicious URL Database: 1.00001(2015-01-01 01:01)
Botnet DB: 1.00000(2012-05-28 22:51)
BIOS version: 05000007
System Part-Number: P21593-03
Log hard disk: Not available
Hostname: FortiGate-300E
Operation Mode: NAT
Current virtual domain: root
Max number of virtual domains: 10
Virtual domains status: 1 in NAT mode, 0 in TP mode
Virtual domain configuration: disable
FIPS-CC mode: disable
Current HA mode: standalone
Branch point: 1112
Release Version Information: GA
FortiOS x86-64: Yes
System time: Thu Dec 21 12:08:41 2023

```

2. **Información del estado de los servicios**
```
get system fortiguard-service status
```
- Este comando proporciona detalles sobre la conectividad y el estado actual de los servicios de FortiGuard (licencias), como:

    - Conexión con FortiGuard
    - Estado de los servicios de actualización
```
FortiGate-300E # get system fortiguard-service status
NAME               VERSION LAST UPDATE          METHOD    EXPIRE
AV Engine           6.144  2020-02-22 01:46:00  manual    n/a
Virus Definitions   90.4713  2022-08-02 15:20:00  manual    n/a
Extended set        90.4713  2022-08-02 15:19:00  manual    n/a
Extreme set         1.000  2018-04-09 18:07:00  manual    n/a
Flow-based Virus Definitions  90.4713  2022-08-02 15:25:00  manual    n/a
Attack Definitions  6.741  2015-12-01 02:30:00  manual    n/a
Attack Extended Definitions  6.741  2015-12-01 02:30:00  manual    n/a
IPS Malicious URL Database  1.001  2015-01-01 01:01:00  manual    n/a
Botnet Definitions  1.000  2012-05-28 22:51:00  manual    n/a
IPS/FlowAV Engine   5.209  2020-05-07 15:50:00  manual    n/a
IPS Config Script   1.009  2019-06-06 14:02:00  manual    n/a
Application Definitions  6.741  2015-12-01 02:30:00  manual    n/a
Industrial Attack Definitions  6.741  2015-12-01 02:30:00  manual    n/a

```

3. **Estado de ventiladores**
```
execute sensor list
```

<details>
<summary>valida que todos los valores "alarm" esten en valor (0).</summary>

```
   FortiGate-300E # execute sensor list
    1 +VCC3             alarm=0  value=3.2896  threshold_status=0
    2 +VCC5             alarm=0  value=5.0172  threshold_status=0
    3 +VCC12            alarm=0  value=11.898  threshold_status=0
    4 DVDD10            alarm=0  value=1.0114  threshold_status=0
    5 NP6_1V15_1        alarm=0  value=1.1662  threshold_status=0
    6 DDR3_VCC1V5_1     alarm=0  value=1.4887  threshold_status=0
    7 NP6_2V5_1         alarm=0  value=2.4918  threshold_status=0
    8 1V0_PHY           alarm=0  value=1.0114  threshold_status=0
    9 VCC10_CP9         alarm=0  value=1.1404  threshold_status=0
    10 P3V3_I/O          alarm=0  value=3.311  threshold_status=0
    11 NP6_P3V3          alarm=0  value=3.2896  threshold_status=0
    12 P1V0_PCH          alarm=0  value=0.992  threshold_status=0
    13 VTT_DDR           alarm=0  value=0.592  threshold_status=0
    14 VCCSA             alarm=0  value=1.04  threshold_status=0
    15 VCCIO             alarm=0  value=0.96  threshold_status=0
    16 +VCORE            alarm=0  value=1.088  threshold_status=0
    17 +VCC_DDR          alarm=0  value=1.2  threshold_status=0
    18 VPP_DDR           alarm=0  value=2.464  threshold_status=0
    19 VCCST             alarm=0  value=0.976  threshold_status=0
    20 CPU DTS0          alarm=0  value=38  threshold_status=0
    21 TD1               alarm=0  value=41  threshold_status=0
    22 TD2               alarm=0  value=42  threshold_status=0
    23 TR3               alarm=0  value=39  threshold_status=0
    24 LM75 U79          alarm=0  value=37  threshold_status=0
    25 LM75 U76          alarm=0  value=40  threshold_status=0
    26 Fan 1             alarm=0  value=6600  threshold_status=0
    27 Fan 2             alarm=0  value=6500  threshold_status=0
    28 Fan 3             alarm=0  value=6500  threshold_status=0
    29 PS1 VIN           alarm=0  value=222  threshold_status=0
    30 PS1 VOUT_12V      alarm=0  value=12.032  threshold_status=0
    31 PS1 Temp 1        alarm=0  value=27  threshold_status=0
    32 PS1 Temp 2        alarm=0  value=29  threshold_status=0
    33 PS1 Fan 1         alarm=0  value=5632  threshold_status=0
    34 PS1 Status        alarm=0
    35 PS2 VIN           alarm=0  (reading unavailable)
    36 PS2 VOUT_12V      alarm=0  (reading unavailable)
    37 PS2 Temp 1        alarm=0  (reading unavailable)
    38 PS2 Temp 2        alarm=0  (reading unavailable)
    39 PS2 Fan 1         alarm=0  (reading unavailable)
    40 PS2 Status        alarm=0  (not detected)

```

</details>

4. **información del rendimiento del sistema**
```
get system performance status
```
- Este comando obtiene información detallada sobre el rendimiento del sistema, proporciona datos como la carga de la CPU, la memoria utilizada, el estado de la interfaz de red, las sesiones activas y otros indicadores clave de rendimiento
    - Uso de la CPU
    - Uso de memoria
    - Estado de las interfaces de red
    - Sesiones activas

```
FortiGate-300E # get system performance status
CPU states: 0% user 1% system 0% nice 99% idle 0% iowait 0% irq 0% softirq
CPU0 states: 0% user 0% system 0% nice 100% idle 0% iowait 0% irq 0% softirq
CPU1 states: 0% user 5% system 0% nice 95% idle 0% iowait 0% irq 0% softirq
CPU2 states: 0% user 0% system 0% nice 100% idle 0% iowait 0% irq 0% softirq
CPU3 states: 0% user 0% system 0% nice 100% idle 0% iowait 0% irq 0% softirq
Memory: 8172040k total, 1600152k used (19.6%), 6371520k free (78.0%), 200368k freeable (2.4%)
Average network usage: 0 / 0 kbps in 1 minute, 0 / 0 kbps in 10 minutes, 0 / 0 kbps in 30 minutes
Average sessions: 0 sessions in 1 minute, 0 sessions in 10 minutes, 0 sessions in 30 minutes
Average session setup rate: 0 sessions per second in last 1 minute, 0 sessions per second in last 10 minutes, 0 sessions per second in last 30 minutes
Average NPU sessions: 0 sessions in last 1 minute, 0 sessions in last 10 minutes, 0 sessions in last 30 minutes
Average nTurbo sessions: 0 sessions in last 1 minute, 0 sessions in last 10 minutes, 0 sessions in last 30 minutes
Virus caught: 0 total in 1 minute
IPS attacks blocked: 0 total in 1 minute
Uptime: 0 days,  2 hours,  51 minutes

```