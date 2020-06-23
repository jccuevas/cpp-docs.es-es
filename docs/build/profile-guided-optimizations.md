---
title: Optimizaciones guiadas por perfiles
ms.date: 04/23/2019
helpviewer_keywords:
- profile-guided optimizations
- optimization, profile-guided [C++]
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
ms.openlocfilehash: 062f8fb8138446e4a00ba6501d6eeb8571625749
ms.sourcegitcommit: 2d7550d0f375aafa428ef0fb2e3962e4232be28e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2020
ms.locfileid: "84777323"
---
# <a name="profile-guided-optimizations"></a>Optimizaciones guiadas por perfiles

La optimización guiada por perfiles (PGO) le permite optimizar un archivo ejecutable completo, donde el optimizador usa datos de las series de pruebas del archivo .exe o .dll. Los datos representan el rendimiento probable del programa en un entorno de producción.

Las optimizaciones guiadas por perfiles solo están disponibles para destinos nativos x86 o x64. No están disponibles para archivos ejecutables que se ejecutan en Common Language Runtime. Aunque produzca un ensamblado con código nativo y administrado mixto (compilado la opción **/clr** del compilador), no puede usar la optimización guiada por perfiles solo en el código nativo. Si intenta compilar un proyecto con estas opciones establecidas en el IDE, se producirá un error de compilación.

> [!NOTE]
> La información que se recopila a partir de series de pruebas de generación de perfiles reemplaza las optimizaciones que, en caso contrario, estarían activas si se especificara **/Ob**, **/Os** o **/Ot**. Para obtener más información, consulte [/Ob (Expansión de funciones insertadas)](reference/ob-inline-function-expansion.md) y [/Os, /Ot (Favorecer código pequeño, favorecer código rápido)](reference/os-ot-favor-small-code-favor-fast-code.md).

## <a name="steps-to-optimize-your-app"></a>Pasos para optimizar la aplicación

Para usar la optimización guiada por perfiles, siga estos pasos para optimizar la aplicación:

- Compile uno o varios archivos de código fuente con [/GL](reference/gl-whole-program-optimization.md).

   Cada módulo compilado con **/GL** se puede examinar durante las series de pruebas de optimización guiada por perfiles para capturar el comportamiento en tiempo de ejecución. No todos los módulos de la compilación de una optimización guiada por perfiles se tienen que compilar con **/GL**. Sin embargo, solo se instrumentarán los módulos compilados con **/GL**, que posteriormente estarán disponibles para optimizaciones guiadas por perfiles.

- Vincule mediante [/LTCG](reference/ltcg-link-time-code-generation.md) y [/GENPROFILE o /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md).

   El uso de **/LTCG** y **/GENPROFILE** o **/FASTGENPROFILE** crea un archivo `.pgd` cuando se ejecuta la aplicación instrumentada. Después de agregar los datos de la serie de pruebas al archivo `.pgd`, se pueden usar como entrada para el siguiente paso del vínculo (la creación de la imagen optimizada). Al especificar **/GENPROFILE**, opcionalmente puede agregar un argumento **PGD=** _filename_ para especificar un nombre o una ubicación no predeterminados para el archivo `.pgd`. La combinación de las opciones **/LTCG** y **/GENPROFILE** o **/FASTGENPROFILE** del enlazador reemplaza a la opción **/LTCG:PGINSTRUMENT** en desuso del enlazador.

- Generar perfiles de la aplicación.

   Cada vez que finaliza una sesión EXE con perfiles generados o se descarga un archivo DLL con perfiles generados, se crea un archivo `appname!N.pgc`. Un archivo `.pgc` contiene información sobre una determinada serie de pruebas de la aplicación. *appname* es el nombre de la aplicación, y *N* es un número a partir de 1 que se incrementa en función del número de otros archivos `appname!N.pgc` que existan en el directorio. Puede eliminar un archivo `.pgc` si la serie de pruebas no representa un escenario que quiere optimizar.

   Durante una serie de pruebas, puede forzar el cierre del archivo `.pgc` abierto en ese momento y la creación de un nuevo archivo `.pgc` con la utilidad [pgosweep](pgosweep.md) (por ejemplo, cuando el final de un escenario de pruebas no coincide con el cierre de la aplicación).

   La aplicación también puede invocar directamente una función PGO, [PgoAutoSweep](pgoautosweep.md), para capturar los datos de perfil en el momento de la llamada como un archivo `.pgc`. Puede proporcionar un control más preciso sobre el código incluido en los datos capturados en sus archivos `.pgc`. Para obtener un ejemplo de cómo usar esta función, consulte la documentación de [PgoAutoSweep](pgoautosweep.md).

   A la hora de crear la compilación instrumentada, la recopilación de datos se realiza en modo no seguro para subprocesos de forma predeterminada, que es el modo más rápido, pero puede ser impreciso. Al usar el argumento **EXACT** para **/GENPROFILE** o **/FASTGENPROFILE**, puede especificar la recopilación de datos en modo seguro para subprocesos, que es más preciso, pero más lento. Esta opción también está disponible si se establece la variable de entorno en desuso [PogoSafeMode](environment-variables-for-profile-guided-optimizations.md#pogosafemode), o la opción del enlazador en desuso **/POGOSAFEMODE**, al crear la compilación instrumentada.

- Vincule mediante **/LTCG** y **/USEPROFILE**.

   Use las opciones **/LTCG** y [/USEPROFILE](reference/useprofile.md) del enlazador para crear la imagen optimizada. Este paso toma como entrada el archivo `.pgd`. Al especificar **/USEPROFILE**, opcionalmente puede agregar un argumento **PGD=** _filename_ para especificar un nombre o una ubicación no predeterminados para el archivo `.pgd`. También puede especificar este nombre mediante la opción **/PGD** en desuso del enlazador. La combinación de **/LTCG** y **/USEPROFILE** reemplaza a las opciones **/LTCG:PGOPTIMIZE** y **/LTCG:PGUPDATE** en desuso del enlazador.

Incluso es posible crear el archivo ejecutable optimizado y, posteriormente, determinar que la generación de perfiles adicionales sería útil para crear una imagen más optimizada. Si la imagen instrumentada y el archivo `.pgd` correspondiente están disponibles, puede efectuar series de pruebas adicionales y recompilar la imagen optimizada con el archivo `.pgd` más reciente mediante el uso de las mismas opciones **/LTCG** y **/USEPROFILE** del enlazador.

> [!NOTE]
> Los archivos `.pgc` y `.pgd` son de tipo binario. Si están almacenados en un sistema de control de código fuente, evite toda transformación automática que se pueda hacer en archivos de texto.

## <a name="optimizations-performed-by-pgo"></a>Optimizaciones realizadas mediante PGO

Las optimizaciones guiadas por perfiles incluyen estas comprobaciones y mejoras:

- **Inserción**: por ejemplo, si una función A llama frecuentemente a la función B y la función B es relativamente pequeña, las optimizaciones guiadas por perfiles insertan la función B en la función A.

- **Especulación de llamada virtual**: si una llamada virtual, u otra llamada a través de un puntero de función, se destina frecuentemente a una función determinada, una optimización guiada por perfiles puede insertar una llamada directa de ejecución condicional a la función de destino frecuente y la llamada directa se puede insertar.

- **Asignación de registros**: la optimización basada en datos de perfil produce una mejor asignación de registros.

- **Optimización básica de bloques**: permite colocar en el mismo conjunto de páginas (emplazamiento) los bloques básicos ejecutados habitualmente que se ejecutan a veces en un marco determinado. Esto minimiza el número de páginas usadas y, por tanto, la sobrecarga de memoria.

- **Optimización del tamaño y la velocidad**: se puede optimizar la velocidad de las funciones en las que el programa invierte más tiempo de ejecución.

- **Diseño de las funciones**: según el gráfico de llamadas y el comportamiento observado entre llamador y destinatario, las funciones que tienden a estar situadas a lo largo de la misma ruta de ejecución se colocan en la misma sección.

- **Optimización de ramas condicionales**: con los sondeos de valor, las optimizaciones guiadas por perfiles pueden averiguar si un valor determinado en una instrucción "switch" se usa con más frecuencia que otros valores.  En tal caso, el valor se puede extraer de la instrucción switch.  Lo mismo se puede hacer con las instrucciones `if`…`else` en las que el optimizador puede ordenar la instrucción `if`…`else` de modo que se coloque primero el bloque `if` o el `else`, en función de cuál sea "true" con más frecuencia.

- **Separación de código no alcanzado**: el código al que no se llama durante la generación de perfiles se mueve a una sección especial que se anexa al final del conjunto de secciones. Mantiene esta sección fuera de las páginas usadas con frecuencia de manera eficaz.

- **Separación de código EH**: dado que el código EH solo se ejecuta de forma excepcional, a menudo se puede mover a una sección independiente. Se mueve cuando las optimizaciones guiadas por perfiles pueden determinar que las excepciones solo se producen en condiciones excepcionales.

- **Funciones intrínsecas de memoria**: la expansión de una función intrínseca depende de si se llama a esta con frecuencia. Una función intrínseca también se puede optimizar basándose en el tamaño de bloque de los movimientos o copias.

## <a name="next-steps"></a>Pasos siguientes

Obtenga más información sobre estas variables de entorno, funciones y herramientas que puede usar en las optimizaciones guiadas por perfiles:

[Variables de entrono para las optimizaciones guiadas por perfiles](environment-variables-for-profile-guided-optimizations.md)<br/>
Estas variables se usaban para especificar el comportamiento en tiempo de ejecución de los escenarios de prueba. Ahora están en desuso y las han reemplazado las nuevas opciones del enlazador. En este documento se muestra cómo pasar de las variables de entorno a las opciones del enlazador.

[PgoAutoSweep](pgoautosweep.md)<br/>
Una función que se puede agregar a la aplicación para proporcionar un control detallado de captura de datos del archivo `.pgc`.

[pgosweep](pgosweep.md)<br/>
Una utilidad de línea de comandos que escribe todos los datos de perfil en el archivo `.pgc`, cierra el archivo `.pgc` y abre un nuevo archivo `.pgc`.

[pgomgr](pgomgr.md)<br/>
Una utilidad de línea de comandos que agrega los datos de perfil de uno o más archivos `.pgc` al archivo `.pgd`.

[Cómo: Combinar varios perfiles PGO en un solo perfil](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)<br/>
Ejemplos de uso de **pgomgr**.

## <a name="see-also"></a>Vea también

[Herramientas de generación MSVC adicionales](reference/c-cpp-build-tools.md)
