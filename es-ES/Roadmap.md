## Hoja de ruta de EOS.IO

Este documento describe el plan de desarrollo a alto nivel y se irá actualizando a medida que se vaya avanzando hacia la versión 1.0. Cabe señalar que esta hoja de ruta se aplica solo al componente Blockchain del software y no a las otras herramientas y utilidades, como wallets y exploradores de bloques, que tendrán sus propios equipos de desarrollo y hojas de ruta dedicados, una vez que se complete la Fase 1.

***Todo lo que se incluye en este documento está en forma de borrador, está sujeto a cambios en cualquier momento y se proporciona únicamente con fines informativos. Block.one no garantiza la exactitud de la información contenida en esta hoja de ruta y la información se proporciona "tal cual" sin representaciones ni garantías, expresas o implícitas.***

# Fase 1 - Entorno de Pruebas Mínimo Viable - Verano del 2017

El objetivo de esta fase es establecer las API que los desarrolladores necesitarán para comenzar a construir y probar aplicaciones en EOS.IO. Para que los desarrolladores comiencen a probar sus aplicaciones requerirán que se implemente lo siguiente:

### Nodo autónomo (Dan & Nathan)

Un nodo autónomo opera una cadena de bloques de prueba y produce bloques exponiendo una API. Este nodo no necesita utilizar código de red P2P.

### Contratos nativos (Nathan)

El software EOS.IO cuenta con varios contratos nativos. Estos son contratos que administran las operaciones centrales de la blockchain y son ajenos a la interfaz Web Assembly. Estos contratos incluyen:

1. @eos: gestiona las transferencias de tokens de EOS
2. @stake - gestiona el Bloqueo de los Tokens de EOS, las Votaciones y la Elección del Productor
3. @system: gestiona permisos, mensajes y las actualizaciones de los códigos de contacto

### API de la Máquina Virtual (Dan)

Los contratos compilados son convertidos a WebAssembly (WASM) y el código WASM interactúa con la blockchain a través de una API definida. Este API, es del que los desarrolladores dependen para crear aplicaciones y será relativamente estable antes de que los desarrolladores realmente puedan comenzar a construir en EOS.

### Interface RPC (Arhag, Nathan)

Se proporcionará una interfaz JSON RPC simple sobre HTTP que permitirá a los desarrolladores difundir transacciones y consultar los estados de las aplicaciones. Esto es crítico tanto para publicar como para interactuar con aplicaciones de prueba.

### Herramientas de línea de comando (Arhag)

Las herramientas de línea de comando facilitan la integración de la interfaz RPC con los entornos de construcción de los desarrolladores.

### Documentación básica del Desarrollador (Josh)

Documentos que enseñen a los desarrolladores cómo comenzar a construir para las blockchains de EOS.IO. Esto incluye documentación del API de WASM, de la interfaz RPC y de las Herramientas de Línea de Comandos.

# Fase 2 - Red de Prueba Mínima Viable - Otoño de 2017

Todo en la Fase 1, presupone trabajar sobre un entorno de confianza en el que solo se ejecuta código de desarrolladores. Antes de implementar una red de pruebas, es necesario implementar y probar varias características adicionales.

### Código para gestión de Red P2P (Phil)

Este es un complemento que se encarga de sincronizar el estado de la cadena de bloques entre nodos autónomos.

### Buen estado de salud del código WASM empleado & Aislamiento de procesos (Brian)

El código WASM debe ser desparasitado, analizando posibles comportamientos no deterministas, como operaciones de punto flotante y bucles infinitos.

### Seguimiento del Uso de Recursos & Límitación mediante Tarificación (Arhag)

Para evitar el abuso, a través de la monitorización de recursos y el seguimiento de su uso, se controlan los limites a los usuarios, en base a su grado de participación en EOS.

### Importación de Génesis para Pruebas (DappHub)

Deberán ser desarrolladas las herramientas, para exportar los datos del estado de Distribución de Tokens de EOS y crear así un archivo Génesis de configuración. Esto permitirá que cualquiera que participe en la Distribución de Tokens, pueda adquirir algún Token inicial para Pruebas EOS (TEOS).

### Comunicación Interblockchain (Nathan)

Esta funcionalidad verifica el hasheado Merkle de las transacciones.

# Fase 3 - Pruebas & Auditorías de Seguridad - Invierno de 2017, Primavera de 2018

Durante esta fase, la plataforma se someterá a pruebas intensivas enfocadas a encontrar problemas de seguridad y errores. Al final de la fase 3, la versión 1.0 quedará etiquetada.

### Desarrollo de Aplicaciones de Ejemplo

Las aplicaciones de ejemplo son fundamentales para probar que la plataforma proporciona las características requeridas por desarrolladores reales.

### Recompensas a Ataques con Éxito en la Red de Pruebas

Atacar la red con spam, exploits (explotación malintencionada) de las máquinas virtuales, bugs responsables de graves interrupciones del sistema (crashes), y comportamientos no deterministas, será un proceso muy complicado pero necesario en pro de garantizar la estabilidad de la versión 1.0.

### Soporte de Lenguajes

Agregando soporte para lenguajes adicionales que puedan ser compilados a WASM: C++, Rust, etc.

### Documentación & Tutoriales

# Fase 4: Optimización de Ejecución en Paralelo - Verano / Otoño de 2018

Tras lanzar un producto 1.0 estable, avanzaremos hacia la optimización del código para la ejecución en paralelo.

# Fase 5 - Implementación de Clúster. El futuro