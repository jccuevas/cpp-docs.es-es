---
title: "Optimizaciones guiadas por perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "optimización, guiadas por perfiles [C++]"
  - "optimizaciones guiadas por perfiles"
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# Optimizaciones guiadas por perfiles
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La optimización guiada por perfiles le permite optimizar un archivo de salida, donde el optimizador utiliza datos de las series de pruebas del archivo .exe o .dll.  Los datos representan el funcionamiento probable del programa en un entorno de producción.  
  
 Las optimizaciones guiadas por perfiles solo están disponibles para destinos nativos x86 o [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)].  Las optimizaciones guiadas por perfiles no están disponibles para archivos de salida que se vayan a ejecutar en Common Language Runtime.  Aunque produzca un ensamblado con código nativo y administrado mixto \(compilado con **\/clr**\), no puede utilizar la optimización guiada por perfiles solo en el código nativo.  Si intentas compilar un proyecto con estas opciones establecidas en el IDE, se producirá un error de compilación.  
  
> [!NOTE]
>  La información que se recopila a partir de las series de pruebas de generación de perfiles reemplazará las optimizaciones que, en caso contrario, estarían activas si se especifica **\/Ob**, **\/Os** u **\/Ot**.  Para obtener más información, consulte [\/Ob \(Expansión de funciones inline\)](../../build/reference/ob-inline-function-expansion.md) y [\/Os, \/Ot \(Favorecer código pequeño, favorecer código rápido\)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md).  
  
 Puede usar el complemento automatizado de optimización guiada por perfiles para Visual C\+\+ en el concentrador de rendimiento y diagnósticos para simplificar y agilizar el proceso de optimización en Visual Studio, o puede realizar manualmente los pasos de optimización en Visual Studio o en la línea de comandos.  Se recomienda el complemento, ya que es más fácil de usar.  Para obtener información sobre cómo obtener el complemento y usarlo para optimizar la aplicación, consulte [Complemento Optimización guiada por perfiles](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md).  
  
 Tanto el complemento de optimización guiada por perfiles como la optimización guiada por perfiles manual siguen estos pasos para optimizar la aplicación:  
  
-   Compilar uno o varios archivos de código fuente con [\/GL](../../build/reference/gl-whole-program-optimization.md).  
  
     Cada módulo compilado con \/GL se puede examinar durante las series de pruebas de optimización guiada por perfiles para capturar el comportamiento en tiempo de ejecución.  No todos los módulos de la compilación de una optimización guiada por perfiles se tienen que compilar con \/GL.  Sin embargo, solo se instrumentarán los módulos compilados con \/GL, que posteriormente estarán disponibles para optimizaciones guiadas por perfiles.  
  
-   Vincular con [\/LTCG:PGINSTRUMENT](../../build/reference/ltcg-link-time-code-generation.md).  
  
     \/LTCG:PGINSTRUMENT crea un archivo .pgd vacío.  Después de agregar los datos de la serie de pruebas al archivo .pgd, se pueden utilizar como entrada para el siguiente paso del vínculo \(creación de la imagen optimizada\).  Al especificar \/LTCG:PGINSTRUMENT, también tiene la opción de especificar [\/PGD](../../build/reference/pgd-specify-database-for-profile-guided-optimizations.md) con un nombre o una ubicación no predeterminados para el archivo .pgd.  
  
-   Generar perfiles de la aplicación.  
  
     Cada vez que finaliza una sesión EXE con perfiles generados o se descarga un archivo DLL con perfiles generados, se crea un archivo *appname*\!\#.pgc.  Un archivo .pgc contiene información sobre una determinada serie de pruebas de la aplicación.  \# es un número a partir de 1, que se incrementa en función del número de otros archivos *appname*\!\#.pgc que existan en el directorio.  Puede eliminar un archivo .pgc si la serie de pruebas no representa un escenario que desea optimizar.  
  
     Durante una serie de pruebas, puede forzar el cierre del archivo .pgc abierto en ese momento y la creación de un nuevo archivo .pgc con la utilidad [pgosweep](../../build/reference/pgosweep.md) \(por ejemplo, cuando el final de un escenario de pruebas no coincide con el cierre de la aplicación\).  
  
     Puede usar la opción `PogoSafeMode` al generar el perfil de la aplicación.  Esta opción permite especificar si desea generar el perfil de la aplicación de modo seguro o rápido.  Para obtener más información sobre estos modos, vea [PogoSafeMode](../../build/reference/pogosafemode.md).  
  
-   Vincular con \/LTCG:PGOPTIMIZE.  
  
     \/LTCG:PGOPTIMIZE crea la imagen optimizada.  Este paso toma como entrada el archivo .pgd.  Para obtener más información, vea [\/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md).  
  
 Incluso es posible crear el archivo de salida optimizado y, posteriormente, determinar que la generación de perfiles adicionales sería útil para crear una imagen más optimizada.  Si la imagen instrumentada y el archivo .pgd correspondientes están disponibles, puede efectuar nuevas series de pruebas y recompilar la imagen optimizada con el archivo .pgd más reciente.  
  
 A continuación se ofrece una lista de las optimizaciones guiadas por perfiles:  
  
-   **Alineación**: por ejemplo, si existe una función A que llama frecuentemente a la función B y la función B es relativamente pequeña, las optimizaciones guiadas por perfiles alinearán la función B con la función A.  
  
-   **Especulación de llamada virtual**: si una llamada virtual, u otra llamada a través de un puntero de función, se destina frecuentemente a una función determinada, una optimización guiada por perfiles puede insertar una llamada directa de ejecución condicional a la función de destino frecuente y la llamada directa se puede alinear.  
  
-   **Asignación de registros**: una optimización con datos de perfil produce la mejor asignación de registros.  
  
-   **Optimización básica de bloques**: la optimización básica de bloques permite colocar en el mismo conjunto de páginas \(emplazamiento\) los bloques básicos ejecutados habitualmente que se ejecutan a veces en un marco determinado.  Así se minimiza el número de páginas utilizado y, por tanto, la sobrecarga de memoria.  
  
-   **Optimización de tamaño y velocidad**: se puede optimizar la velocidad de las funciones para las que el programa necesita mucho tiempo.  
  
-   **Diseño de funciones**: según el gráfico de llamadas y el comportamiento observado entre llamador y destinatario, las funciones que tienden a estar situadas a lo largo de la misma ruta de ejecución se colocan en la misma sección.  
  
-   **Optimización de bifurcaciones condicionales**: con las comprobaciones de valores, las optimizaciones guiadas por perfiles pueden averiguar si un valor determinado en una instrucción switch se utiliza con más frecuencia que otros valores.  En tal caso, el valor se puede extraer de la instrucción switch.  Lo mismo se puede hacer con las instrucciones if\-else en las que el optimizador puede ordenar la instrucción if\-else de modo que se coloque primero el bloque if o el else, en función de cuál sea true con más frecuencia.  
  
-   **Separación de código no alcanzado**: el código al que no se llama durante la generación de perfiles se mueve a una sección especial que se anexa al final del conjunto de secciones.  Así, esta sección se mantiene fuera de las páginas utilizadas con frecuencia de manera efectiva.  
  
-   **Separación de código EH**: el código EH, que se ejecuta excepcionalmente, a menudo se puede mover a una sección independiente cuando las optimizaciones guiadas por perfiles pueden determinar que las excepciones solo se producen bajo condiciones especiales.  
  
-   **Funciones intrínsecas de memoria**: la expansión de funciones intrínsecas se puede decidir mejor cuando es posible determinar si se llama a una función intrínseca con frecuencia.  Una función intrínseca también se puede optimizar basándose en el tamaño de bloque de los movimientos o copias.  
  
 Para obtener más información sobre la realización de la optimización manual en el IDE o en la línea de comandos, consulte [Tutorial: Usar optimizaciones guiadas por perfiles](http://msdn.microsoft.com/es-es/6e36421b-ec8c-4626-9c29-fa5ffb6f27f8).  
  
## En esta sección  
 [Complemento Optimización guiada por perfiles](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md)  
  
 [Herramientas para la optimización basada en perfiles](../../build/reference/tools-for-manual-profile-guided-optimization.md)  
  
 [Cómo: Combinar varios perfiles PGO en un solo perfil](../../build/reference/how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)  
  
## Vea también  
 [Herramientas de compilación de C\/C\+\+](../../build/reference/c-cpp-build-tools.md)