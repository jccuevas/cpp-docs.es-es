---
title: Optimizaciones guiadas por perfiles | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- profile-guided optimizations
- optimization, profile-guided [C++]
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f2d72ddda460a88830f7f7692f4c9707fa3101a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="profile-guided-optimizations"></a>Optimizaciones guiadas por perfiles
La optimización guiada por perfiles le permite optimizar un archivo de salida, donde el optimizador utiliza datos de las series de pruebas del archivo .exe o .dll. Los datos representan el funcionamiento probable del programa en un entorno de producción.  
  
 Las optimizaciones guiadas por perfiles solo están disponibles para destinos nativos x86 o [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)]. Las optimizaciones guiadas por perfiles no están disponibles para archivos de salida que se vayan a ejecutar en Common Language Runtime. Aunque produzca un ensamblado con código nativo y administrado mixto (compilar con **/CLR**), no puede utilizar la optimización guiada por perfiles solo en el código nativo. Si intentas compilar un proyecto con estas opciones establecidas en el IDE, se producirá un error de compilación.  
  
> [!NOTE]
>  Información que se recopila de ejecuciones de pruebas de generación de perfiles reemplazará las optimizaciones que en caso contrario, estarían activas si se especifica **/Ob**, **/Os**, o **/Ot**. Para obtener más información, consulte [/Ob (expansión de funciones Inline)](../../build/reference/ob-inline-function-expansion.md) y [/Os, /Ot (favorecer código pequeño, favorecer código rápido)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md).  
  
 Puede usar el complemento automatizado de optimización guiada por perfiles para Visual C++ en el concentrador de rendimiento y diagnósticos para simplificar y agilizar el proceso de optimización en Visual Studio, o puede realizar manualmente los pasos de optimización en Visual Studio o en la línea de comandos. Se recomienda el complemento, ya que es más fácil de usar. Para obtener información acerca de cómo obtener el complemento y usarlo para optimizar la aplicación, consulte [complemento de optimización guiada por perfiles](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md).  
  
 Tanto el complemento de optimización guiada por perfiles como la optimización guiada por perfiles manual siguen estos pasos para optimizar la aplicación:  
  
-   Compilar uno o más archivos de código fuente con [/GL](../../build/reference/gl-whole-program-optimization.md).  
  
     Cada módulo compilado con /GL se puede examinar durante las series de pruebas de optimización guiada por perfiles para capturar el comportamiento en tiempo de ejecución. No todos los módulos de la compilación de una optimización guiada por perfiles se tienen que compilar con /GL. Sin embargo, solo se instrumentarán los módulos compilados con /GL, que posteriormente estarán disponibles para optimizaciones guiadas por perfiles.  
  
-   Vincular mediante [/LTCG](../../build/reference/ltcg-link-time-code-generation.md) y [/genprofile](../../build/reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md).  
  
     El uso de /LTCG y/genprofile, crea un archivo .pgd vacío. Después de agregar los datos de la serie de pruebas al archivo .pgd, se pueden utilizar como entrada para el siguiente paso del vínculo (creación de la imagen optimizada). Cuando se especifica/genprofile, puede agregar opcionalmente: PGD =`filename` para especificar un nombre no predeterminado o la ubicación para el archivo. pgd.  
  
-   Generar perfiles de la aplicación.  
  
     Cada vez que finaliza una sesión EXE con perfiles o se descarga un archivo DLL para un *appname*! #. pgc se crea. Un archivo .pgc contiene información sobre una determinada serie de pruebas de la aplicación. # es un número a partir de 1, que se incrementa en función del número de otros *appname*! # .pgc que existan los archivos en el directorio. Puede eliminar un archivo .pgc si la serie de pruebas no representa un escenario que desea optimizar.  
  
     Durante la ejecución de prueba, puede forzar el cierre del archivo .pgc abierto actualmente y la creación de un nuevo archivo .pgc con la [pgosweep](../../build/reference/pgosweep.md) utilidad (por ejemplo, al final de un escenario de prueba no coincide con el cierre de la aplicación).  
  
     Puede usar la opción `PogoSafeMode` al generar el perfil de la aplicación. Esta opción permite especificar si desea generar el perfil de la aplicación de modo seguro o rápido. Para obtener más información acerca de estos modos, consulte [PogoSafeMode](../../build/reference/pogosafemode.md).  
  
-   Vincular con/LTCG y/useprofile.  
  
     Uso de /LTCG y/useprofile crea la imagen optimizada. Este paso toma como entrada el archivo .pgd. Cuando se especifica/useprofile, puede agregar opcionalmente: PGD =`filename` para especificar un nombre no predeterminado o la ubicación para el archivo. pgd. Para obtener más información, consulte [/LTCG](../../build/reference/ltcg-link-time-code-generation.md).  
  
 Incluso es posible crear el archivo de salida optimizado y, posteriormente, determinar que la generación de perfiles adicionales sería útil para crear una imagen más optimizada. Si la imagen instrumentada y el archivo .pgd correspondientes están disponibles, puede efectuar nuevas series de pruebas y recompilar la imagen optimizada con el archivo .pgd más reciente.  
  
 A continuación se ofrece una lista de las optimizaciones guiadas por perfiles:  
  
-   **Inclusión** : por ejemplo, si existe una función A que con frecuencia llama a la función B y la función B es relativamente pequeña, a continuación, las optimizaciones guiadas por perfil funcionarán en línea B en la función A.  
  
-   **Especulación de llamada virtual** -si una llamada virtual, u otra llamada a través de un puntero a función, se destina frecuentemente a una función determinada, una optimización guiada por perfiles puede insertar una llamada directa a la función de destino frecuente, ejecución condicional y la llamada directa se puede alinear.  
  
-   **Asignación de registros** : optimización con datos de perfil produce una mejor asignación de registro.  
  
-   **Optimización básica de bloques** -optimización básica de bloques permite bloques básicos ejecutados habitualmente que se ejecutan dentro de un período determinado que se colocarán en el mismo conjunto de páginas (emplazamiento). Así se minimiza el número de páginas utilizado y, por tanto, la sobrecarga de memoria.  
  
-   **Optimización de tamaño y velocidad** -funciones que el programa necesita mucho tiempo se pueden optimizar para acelerar el proceso.  
  
-   **Diseño de funciones** : basado en el gráfico de llamadas y generar perfiles de comportamiento de llamador y destinatario, las funciones que tienden a ser a lo largo de la misma ruta de acceso de ejecución se colocan en la misma sección.  
  
-   **Optimización de bifurcaciones condicionales** : con las comprobaciones de valores, guiada por perfiles pueden encontrar las optimizaciones si un valor determinado en una instrucción switch se utiliza con más frecuencia que otros valores.  En tal caso, el valor se puede extraer de la instrucción switch.  Lo mismo se puede hacer con las instrucciones if-else en las que el optimizador puede ordenar la instrucción if-else de modo que se coloque primero el bloque if o el else, en función de cuál sea true con más frecuencia.  
  
-   **Separación de código no alcanzado** -código que no se llama durante la generación de perfiles se mueve a una sección especial que se anexa al final del conjunto de secciones. Así, esta sección se mantiene fuera de las páginas utilizadas con frecuencia de manera efectiva.  
  
-   **Separación de código EH** -el código EH, que se ejecuta excepcionalmente, a menudo se puede mover a una sección independiente cuando las optimizaciones guiadas por perfiles pueden determinar que las excepciones solo se producen bajo condiciones especiales.  
  
-   **Funciones intrínsecas de memoria** -la expansión de funciones intrínsecas se puede decidir mejor si se puede determinar si una función intrínseca se llama con frecuencia. Una función intrínseca también se puede optimizar basándose en el tamaño de bloque de los movimientos o copias.  
  
 Para obtener más información acerca de la realización optimización manual en el IDE o en la línea de comandos, consulte [complemento de optimización guiada por perfiles](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md).  
  
## <a name="in-this-section"></a>En esta sección  
 [Complemento optimización guiada por perfiles](../../build/reference/profile-guided-optimization-in-the-performance-and-diagnostics-hub.md)  
  
 [Herramientas para la optimización manual guiada por perfiles](../../build/reference/tools-for-manual-profile-guided-optimization.md)  
  
 [Cómo: Combinar varios perfiles PGO en un solo perfil](../../build/reference/how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)  
  
## <a name="see-also"></a>Vea también  
 [Herramientas de compilación de C/C++](../../build/reference/c-cpp-build-tools.md)