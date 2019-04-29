---
title: Optimizaciones guiadas por perfil
ms.date: 04/23/2019
helpviewer_keywords:
- profile-guided optimizations
- optimization, profile-guided [C++]
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
ms.openlocfilehash: 46619e77861b6a3a78d74ce6c6d9173a3a5f270f
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341151"
---
# <a name="profile-guided-optimizations"></a>Optimizaciones guiadas por perfil

Optimización guiada por perfiles (PGO) le permite optimizar un archivo ejecutable completamente, donde el optimizador utiliza datos de series de pruebas del archivo .exe o .dll. Los datos representan el rendimiento probable del programa en un entorno de producción.

Las optimizaciones guiadas por perfiles solo están disponibles para destinos nativos x86 o x64. Las optimizaciones guiadas por perfiles no están disponibles para los archivos ejecutables que se ejecutan en common language runtime. Aunque genere un ensamblado con código nativo y administrado mixto (mediante el uso de la **/CLR** opción del compilador), no se puede usar la optimización guiada por perfiles en simplemente el código nativo. Si intenta compilar un proyecto con estas opciones establecidas en el IDE, se producirá un error de compilación.

> [!NOTE]
> Información recopilada de ejecuciones de pruebas de generación de perfiles reemplazará las optimizaciones que en caso contrario, estarían activas si se especifica **/Ob**, **/Os**, o **/Ot**. Para obtener más información, consulte [/Ob (expansión de funciones insertadas)](reference/ob-inline-function-expansion.md) y [/Os, /Ot (favorecer código pequeño, favorecer código rápido)](reference/os-ot-favor-small-code-favor-fast-code.md).

## <a name="steps-to-optimize-your-app"></a>Pasos para optimizar la aplicación

Para usar la optimización guiada por perfiles, siga estos pasos para optimizar la aplicación:

- Compilar uno o varios archivos de código fuente con [/GL](reference/gl-whole-program-optimization.md).

   Cada módulo compilado con **/GL** se puede examinar durante las ejecuciones de pruebas de optimización guiada por perfiles para capturar el comportamiento de tiempo de ejecución. Cada módulo en una compilación de optimización guiada por perfiles no tiene que compilarse con **/GL**. Sin embargo, solo los módulos compilan con **/GL** están instrumentadas y posteriormente estarán disponibles para optimizaciones guiadas por perfil.

- Vincúlelo con [/LTCG](reference/ltcg-link-time-code-generation.md) y [/GENPROFILE o/fastgenprofile](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md).

   Con ambos **/LTCG** y **/genprofile** o **/fastgenprofile** crea un `.pgd` archivo cuando se ejecuta la aplicación instrumentada. Después de agregar datos de ejecución de pruebas para el `.pgd` archivo, se puede usar como entrada para el siguiente paso del vínculo (creación de la imagen optimizada). Al especificar **/genprofile**, opcionalmente, puede agregar un **PGD =**_filename_ argumento para especificar un nombre no predeterminado o una ubicación para el `.pgd` archivo. La combinación de **/LTCG** y **/genprofile** o **/fastgenprofile** opciones del vinculador reemplaza al elemento desusado **/LTCG: PGINSTRUMENT** opción del vinculador.

- Generar perfiles de la aplicación.

   Finaliza una sesión EXE con perfiles de cada vez, o un archivo DLL de generación de perfiles se descarga, un `appname!N.pgc` se crea el archivo. Un `.pgc` archivo contiene información sobre una serie de pruebas de aplicación determinada. *appname* es el nombre de la aplicación, y *N* es un número que empieza con 1 que se incrementa en función del número de otros `appname!N.pgc` archivos en el directorio. Puede eliminar un `.pgc` archivo si la ejecución de pruebas no representan un escenario que desea optimizar.

   Durante una ejecución de pruebas, puede forzar el cierre de abiertos actualmente `.pgc` archivo y la creación de un nuevo `.pgc` de archivos con la [pgosweep](pgosweep.md) utilidad (por ejemplo, al final de un escenario de prueba no coincide con la aplicación apagado).

   La aplicación directamente también puede invocar una función PGO, [PgoAutoSweep](pgoautosweep.md), para capturar los datos de perfil en el momento de la llamada como un `.pgc` archivo. Puede proporcionarle un mayor control sobre el código de los datos capturados en su `.pgc` archivos. Para obtener un ejemplo de cómo usar esta función, vea el [PgoAutoSweep](pgoautosweep.md) documentación.

   Cuando se crea la compilación instrumentada, de forma predeterminada, la recopilación de datos se realiza en modo no seguro para subprocesos, que es más rápido, pero puede ser impreciso. Mediante el uso de la **EXACT** argumento **/genprofile** o **/fastgenprofile**, puede especificar la recopilación de datos en modo seguro para subprocesos, que es más preciso, pero más lento. Esta opción también está disponible si se establece en desuso [PogoSafeMode](environment-variables-for-profile-guided-optimizations.md#pogosafemode) variable de entorno o en desuso **/PogoSafeMode** opción del vinculador, cuando se crea la compilación instrumentada.

- Vincúlelo con **/LTCG** y **/useprofile**.

   Usar tanto el **/LTCG** y [/useprofile](reference/useprofile.md) opciones del enlazador para crear la imagen optimizada. Este paso toma como entrada el `.pgd` archivo. Al especificar **/useprofile**, opcionalmente, puede agregar un **PGD =**_filename_ argumento para especificar un nombre distinto del predeterminado o una ubicación para el `.pgd` archivo. También puede especificar este nombre mediante el uso del objeto desusado **/PGD** opción del vinculador. La combinación de **/LTCG** y **/useprofile** reemplaza al elemento desusado **/LTCG: PGOPTIMIZE** y **/LTCG: PGUPDATE** opciones del vinculador.

Es posible incluso crear el archivo ejecutable optimizado y posteriormente, determinar que la generación de perfiles adicionales sería útil para crear una imagen más optimizada. Si la imagen instrumentada y su `.pgd` archivo están disponibles, puede realizar series de pruebas adicionales y volver a generar la imagen optimizada con las versiones más recientes `.pgd` archivo con el mismo **/LTCG** y   **/useprofile** opciones del vinculador.

## <a name="optimizations-performed-by-pgo"></a>Optimizaciones realizadas por PGO

Las optimizaciones guiadas por perfiles incluyen estas comprobaciones y mejoras:

- **Inserción** ; por ejemplo, si una función A frecuentemente llama a la función B y la función B es relativamente pequeño, a continuación, guiada por perfiles optimizaciones función insertada B en función de r.

- **Especulación de llamada virtual** -si una llamada virtual, u otra llamada a través de un puntero a función, se destina frecuentemente a una función determinada, una optimización guiada por perfiles puede insertar una llamada directa ejecutada condicionalmente a la función de destino con frecuencia, y la llamada directa se puede alinear.

- **Asignación de registros** -optimización según los resultados de datos de perfil en la mejor asignación de registros.

- **Optimización básica de bloques** -optimización básica de bloques permite bloques básicos ejecutados habitualmente que se ejecutan dentro de un intervalo que se colocarán en el mismo conjunto de páginas (emplazamiento) temporalmente. Minimiza el número de páginas utilizadas, lo que minimiza la sobrecarga de memoria.

- **Optimización de tamaño y velocidad** -funciones que el programa necesita más tiempo de ejecución pueden optimizarse para acelerar el proceso.

- **Diseño de funciones** : basándose en el gráfico de llamadas y generando el perfil de comportamiento de llamador y destinatario, las funciones que tienden a ser a lo largo de la misma ruta de ejecución se colocan en la misma sección.

- **Optimización de bifurcaciones condicionales** : con las comprobaciones de valores, guiada por perfiles pueden encontrar las optimizaciones si un valor determinado en una instrucción switch se utiliza con más frecuencia que otros valores.  En tal caso, el valor se puede extraer de la instrucción switch.  Lo mismo se puede hacer con `if`... `else` instrucciones donde el optimizador puede ordenar la `if`... `else` hasta que ya sea el `if` o `else` bloque se coloca en primer lugar, dependiendo de cuál es más frecuentemente es true.

- **Separación de código muerto** -código que no se llama durante la generación de perfiles se mueve a una sección especial que se anexa al final del conjunto de secciones. Esta sección fuera de las páginas utilizadas con frecuencia mantiene eficazmente.

- **Separación de código EH** -excepcionalmente solo se ejecuta código EH porque, a menudo se pueden mover a una sección independiente. Se mueve cuando las optimizaciones guiadas por perfiles pueden determinar que las excepciones se producen solo en condiciones excepcionales.

- **Funciones intrínsecas de memoria** : expandir el intrínseco o no depende de si se llama con frecuencia. Una función intrínseca también se puede optimizar basándose en el tamaño de bloque de los movimientos o copias.

## <a name="next-steps"></a>Pasos siguientes

Más información acerca de estas variables de entorno, funciones y herramientas que puede usar en las optimizaciones guiadas por perfiles:

[Variables de entorno para las optimizaciones guiadas por perfil](environment-variables-for-profile-guided-optimizations.md)<br/>
Estas variables se usan para especificar el comportamiento de tiempo de ejecución de escenarios de pruebas. Ahora que están en desuso y reemplazados por nuevas opciones del vinculador. Este documento muestra cómo pasar de las variables de entorno para las opciones del vinculador.

[PgoAutoSweep](pgoautosweep.md)<br/>
Una función puede agregar a la aplicación para proporcionar personalización avanzada `.pgc` control de la captura de datos de archivo.

[pgosweep](pgosweep.md)<br/>
Una utilidad de línea de comandos que escribe todos los datos de perfil en el `.pgc` de archivos, se cierra el `.pgc` de archivos y abre una nueva `.pgc` archivo.

[pgomgr](pgomgr.md)<br/>
Una utilidad de línea de comandos que agrega datos de perfil de uno o varios `.pgc` archivos a la `.pgd` archivo.

[Cómo: Combinar varios perfiles PGO en un solo perfil](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)<br/>
Ejemplos de **pgomgr** uso.

## <a name="see-also"></a>Vea también

[Herramientas de generación MSVC adicionales](reference/c-cpp-build-tools.md)
