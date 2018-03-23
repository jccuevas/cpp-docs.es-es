---
title: Optimizaciones guiadas por perfiles | Documentos de Microsoft
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- profile-guided optimizations
- optimization, profile-guided [C++]
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8ca4c79fd46954d59a8fdd892fabbd53d4bc985f
ms.sourcegitcommit: ee7d74683af7631441c8c7f65ef5ceceaee4a5ee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="profile-guided-optimizations"></a>Optimizaciones guiadas por perfiles

La optimización guiada por perfiles le permite optimizar un archivo de salida, donde el optimizador utiliza datos de las series de pruebas del archivo .exe o .dll. Los datos representan el funcionamiento probable del programa en un entorno de producción.

Las optimizaciones guiadas por perfiles solo están disponibles para destinos nativos x86 o x x64. Las optimizaciones guiadas por perfiles no están disponibles para los archivos de salida que se ejecutan en common language runtime. Aunque produzca un ensamblado con código nativo y administrado mixto (mediante el uso de la **/CLR** opción del compilador), no puede utilizar la optimización guiada por perfiles solo en el código nativo. Si intenta compilar un proyecto con estas opciones establecidas en el IDE, se produce un error de compilación.

> [!NOTE]
> Información que se recopila de ejecuciones de pruebas de generación de perfiles reemplazará las optimizaciones que en caso contrario, estarían activas si se especifica **/Ob**, **/Os**, o **/Ot**. Para obtener más información, consulte [/Ob (expansión de funciones Inline)](../../build/reference/ob-inline-function-expansion.md) y [/Os, /Ot (favorecer código pequeño, favorecer código rápido)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md).

## <a name="steps-to-optimize-your-app"></a>Pasos para optimizar la aplicación

Para utilizar la optimización guiada por perfiles, siga estos pasos para optimizar la aplicación:

- Compilar uno o más archivos de código fuente con [/GL](../../build/reference/gl-whole-program-optimization.md).

   Cada módulo compilado con **/GL** se pueden examinar durante las ejecuciones de prueba de optimización guiada por perfiles para capturar el comportamiento de tiempo de ejecución. Cada módulo en una compilación de optimización guiada por perfiles no tienen que compilarse con **/GL**. Sin embargo, solo los módulos compilan con **/GL** están instrumentadas y posteriormente estarán disponibles para optimizaciones guiadas por perfiles.

- Vincular mediante [/LTCG](../../build/reference/ltcg-link-time-code-generation.md) y [/GENPROFILE o/fastgenprofile](../../build/reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md).

   Utilizar **/LTCG** y **/genprofile** o **/fastgenprofile** crea un archivo .pgd cuando se ejecuta la aplicación instrumentada. Después de agregar los datos de la serie de pruebas al archivo .pgd, se pueden utilizar como entrada para el siguiente paso del vínculo (creación de la imagen optimizada). Al especificar **/genprofile**, puede agregar opcionalmente una **PGD =**_filename_ argumento para especificar un nombre no predeterminado o la ubicación para el archivo. pgd. La combinación de **/LTCG** y **/genprofile** o **/fastgenprofile** opciones del vinculador reemplaza las regiones **/LTCG: PGINSTRUMENT** opción del vinculador.

- Generar perfiles de la aplicación.

   Cada vez que finaliza una sesión EXE con perfiles o se descarga un archivo DLL para un *appname*! #. pgc se crea. Un archivo .pgc contiene información sobre una determinada serie de pruebas de la aplicación. # es un número a partir de 1, que se incrementa en función del número de otros *appname*! # .pgc que existan los archivos en el directorio. Puede eliminar un archivo .pgc si la serie de pruebas no representa un escenario que desea optimizar.

   Durante la ejecución de prueba, puede forzar el cierre del archivo .pgc abierto actualmente y la creación de un nuevo archivo .pgc con la [pgosweep](../../build/reference/pgosweep.md) utilidad (por ejemplo, al final de un escenario de prueba no coincide con el cierre de la aplicación).

   La aplicación directamente también puede invocar una función PGO, [PgoAutoSweep](pgoautosweep.md), para capturar los datos de perfil en el momento de la llamada como un archivo .pgc. Esto puede proporcionar un control más preciso sobre el código cubierto por los datos capturados en los archivos .pgc que existan. Para obtener un ejemplo de cómo usar esta función, consulte el [PgoAutoSweep](pgoautosweep.md) documentación.

   Cuando se crea la compilación instrumentada, de forma predeterminada, se realiza la recopilación de datos en modo no seguro para subprocesos, que es más rápido, pero puede que no sea completamente exacto. Mediante el uso de la **EXACT** argumento pasado a **/genprofile** o **/fastgenprofile**, puede especificar la recolección de datos en modo seguro para subprocesos, que es más preciso pero más lento. Esta opción también está disponible si se establece el desuso [PogoSafeMode](environment-variables-for-profile-guided-optimizations.md#pogosafemode) variable de entorno o las regiones **/POGOSAFEMODE** opción del vinculador, cuando se crea la compilación instrumentada.

- Vincular mediante **/LTCG** y **/useprofile**.

   Usar el **/LTCG** y [/useprofile](useprofile.md) opciones del vinculador para crear la imagen optimizada. Este paso toma como entrada el archivo .pgd. Cuando se especifica **/useprofile**, puede agregar opcionalmente una **PGD =**_filename_ argumento para especificar un nombre distinto del predeterminado o una ubicación para el archivo. pgd. También puede especificar este nombre mediante el uso de las regiones **/PGD** opción del vinculador. La combinación de **/LTCG** y **/useprofile** reemplaza las regiones **/LTCG: PGOPTIMIZE** y **/LTCG: PGUPDATE** opciones del vinculador.

Incluso es posible crear el archivo de salida optimizado y, posteriormente, determinar que la generación de perfiles adicionales sería útil para crear una imagen más optimizada. Si la imagen instrumentada y el archivo .pgd correspondientes están disponibles, puede hacerlo nuevas series de pruebas y volver a generar la imagen optimizada con el archivo .pgd más reciente, con la misma **/LTCG** y **/useprofile** opciones del vinculador .

## <a name="optimizations-performed-by-pgo"></a>Optimizaciones realizadas por PGO

A continuación se ofrece una lista de las optimizaciones guiadas por perfiles:

- **Inclusión** : por ejemplo, si existe una función A que con frecuencia llama a la función B y la función B es relativamente pequeña, a continuación, las optimizaciones guiadas por perfil funcionarán en línea B en la función A.

- **Especulación de llamada virtual** -si una llamada virtual, u otra llamada a través de un puntero a función, se destina frecuentemente a una función determinada, una optimización guiada por perfiles puede insertar una llamada directa a la función de destino frecuente, ejecución condicional y la llamada directa se puede alinear.

- **Asignación de registros** : optimización con datos de perfil produce una mejor asignación de registro.

- **Optimización básica de bloques** -optimización básica de bloques permite bloques básicos ejecutados habitualmente que se ejecutan dentro de un período determinado que se colocarán en el mismo conjunto de páginas (emplazamiento). Así se minimiza el número de páginas utilizado y, por tanto, la sobrecarga de memoria.

- **Optimización de tamaño y velocidad** -funciones que el programa necesita mucho tiempo se pueden optimizar para acelerar el proceso.

- **Diseño de funciones** : basado en el gráfico de llamadas y generar perfiles de comportamiento de llamador y destinatario, las funciones que tienden a ser a lo largo de la misma ruta de acceso de ejecución se colocan en la misma sección.

- **Optimización de bifurcaciones condicionales** : con las comprobaciones de valores, guiada por perfiles pueden encontrar las optimizaciones si un valor determinado en una instrucción switch se utiliza con más frecuencia que otros valores.  En tal caso, el valor se puede extraer de la instrucción switch.  Lo mismo se puede hacer con las instrucciones if-else en las que el optimizador puede ordenar la instrucción if-else de modo que se coloque primero el bloque if o el else, en función de cuál sea true con más frecuencia.

- **Separación de código no alcanzado** -código que no se llama durante la generación de perfiles se mueve a una sección especial que se anexa al final del conjunto de secciones. Así, esta sección se mantiene fuera de las páginas utilizadas con frecuencia de manera efectiva.

- **Separación de código EH** -el código EH, que se ejecuta excepcionalmente, a menudo se puede mover a una sección independiente cuando las optimizaciones guiadas por perfiles pueden determinar que las excepciones solo se producen bajo condiciones especiales.

- **Funciones intrínsecas de memoria** -la expansión de funciones intrínsecas se puede decidir mejor si se puede determinar si una función intrínseca se llama con frecuencia. Una función intrínseca también se puede optimizar basándose en el tamaño de bloque de los movimientos o copias.

Si usa Visual Studio 2013, puede usar el automatizadas [complemento de optimización guiada por perfiles](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md) de Visual C++ en el Hub rendimiento y diagnósticos para simplificar y agilizar el proceso de optimización en Visual Studio. Este complemento no está disponible en versiones posteriores de Visual Studio.

## <a name="next-steps"></a>Pasos siguientes

Más información acerca de estas variables de entorno, funciones y herramientas que puede usar en las optimizaciones guiadas por perfil:

[Variables de entorno para las optimizaciones guiadas por perfiles](../../build/reference/environment-variables-for-profile-guided-optimizations.md)<br/>
Estas variables se pueden utilizar para especificar el comportamiento de tiempo de ejecución de escenarios de pruebas. Se ha quedado en desuso en favor de nuevas opciones del vinculador; Lea esta opción para ayudarle a pasar de las variables de entorno para las opciones del vinculador.

[PgoAutoSweep](pgoautosweep.md)<br/>
Una función que puede agregar a la aplicación para proporcionar el control de captura de datos de archivo .pgc específica.

[pgosweep](../../build/reference/pgosweep.md)<br/>
Una utilidad de línea de comandos que escribe todos los datos de perfil en el archivo .pgc, cierra el archivo .pgc y abre un nuevo archivo .pgc.

[pgomgr](../../build/reference/pgomgr.md)<br/>
Una utilidad de línea de comandos que agrega datos de perfil desde uno o más archivos .pgc al archivo .pgd.

[Cómo: combinar varios perfiles PGO en un solo perfil](../../build/reference/how-to-merge-multiple-pgo-profiles-into-a-single-profile.md) ejemplos de **pgomgr** uso.

## <a name="see-also"></a>Vea también

[Herramientas de compilación de C/C++](../../build/reference/c-cpp-build-tools.md)
