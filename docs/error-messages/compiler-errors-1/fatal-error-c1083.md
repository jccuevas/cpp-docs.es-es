---
title: "Error irrecuperable C1083 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1083"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1083"
ms.assetid: 97e52df3-e79c-4f85-8f1e-bbd1057d55e7
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1083
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

No se puede abrir el archivo tipodearchivo: 'archivo': mensaje  
  
 El compilador genera un error C1083 cuando no puede encontrar un archivo. Estos son los motivos habituales por los que el compilador genera este error.  
  
 **El nombre de archivo especificado es incorrecto**  
  
 El nombre de un archivo está mal escrito. Por ejemplo,  
  
```cpp  
#include <algorithms.h>  
```  
  
 no se encuentra el archivo deseado. Hay un archivo de encabezado Biblioteca estándar de C++ denominado algoritmos que no tiene una extensión de nombre de archivo .h. Esta directiva `include` no encontraría ese archivo. Para corregir este problema, compruebe que el nombre de archivo está escrito correctamente.  
  
 Algunos encabezados de la biblioteca de C en tiempo de ejecución se encuentran en un subdirectorio del directorio de inclusión estándar. Por ejemplo, para incluir sys\types.h, debe incluir el nombre del subdirectorio sys en la directiva Include:  
  
 `#include <sys\types.h>`  
  
 **El archivo no está incluido en la ruta de acceso de búsqueda del compilador**  
  
 El compilador no puede encontrar el archivo utilizando las reglas de búsqueda establecidas por una directiva `include` o `import`. Por ejemplo, un nombre de archivo de encabezado incluido entre comillas.  
  
 `#include "myincludefile.h"`  
  
 le indica al compilador que busque primero el archivo en el mismo directorio que contiene el archivo de origen y que luego busque en otras ubicaciones especificadas por el entorno de compilación. Si las comillas contienen una ruta de acceso absoluta, el compilador solo busca el archivo en esa ubicación. Si las comillas contienen una ruta de acceso relativa, el compilador busca el archivo en el directorio relativo al directorio de origen. Si el nombre está incluido entre corchetes angulares  
  
 `#include <stdio.h>`  
  
 el compilador sigue una ruta de acceso de búsqueda definida por el entorno de compilación, el **/I** opción del compilador, el **/X** opción del compilador y la **INCLUDE** variable de entorno. Para obtener más información, incluidos detalles concretos sobre el orden de búsqueda usado para buscar un archivo, consulte [#include (directiva) (C/C ++)](../../preprocessor/hash-include-directive-c-cpp.md) y [#import (directiva)](../../preprocessor/hash-import-directive-cpp.md).  
  
 Incluso si los archivos de encabezado se indican en **el Explorador de soluciones** como parte de un proyecto, los archivos solo se encuentran por el compilador cuando se conocen por un `include` o `import` Directiva y están ubicados en una ruta de acceso de búsqueda de directorio. Los diferentes tipos de compilaciones podrían usar distintas rutas de búsqueda. El **/X** opción del compilador puede utilizarse para excluir directorios de la ruta de búsqueda de archivos de inclusión. Esto permite que distintas compilaciones puedan usar diferentes archivos de inclusión que tienen el mismo nombre, pero se mantienen en directorios distintos. Ésta es una alternativa a la compilación condicional utilizando los comandos de preprocesador. Para obtener más información sobre la **/X** opción del compilador, vea [/X (omitir estándar incluyen rutas de acceso)](../../build/reference/x-ignore-standard-include-paths.md).  
  
 Cuando el compilador se invoca en la línea de comandos, suelen usarse las variables de entorno para especificar rutas de búsqueda. Si la ruta de acceso de búsqueda descrita por la **INCLUDE** variable de entorno no está configurada correctamente, se genera un error C1083. Para obtener más información sobre cómo usar las variables de entorno, vea [Cómo: utilizar Variables de entorno en una compilación](../Topic/How%20to:%20Use%20Environment%20Variables%20in%20a%20Build.md).  
  
 Para corregir este problema, corrija la ruta que el compilador utiliza para buscar el archivo incluido o importado. Un nuevo proyecto utiliza las rutas de búsqueda predeterminadas. Es posible que tenga que modificar la ruta de acceso que se va a agregar un directorio para el proyecto. Si realiza la compilación en la línea de comandos, establezca la **INCLUDE** variable de entorno o el **/I** opción del compilador para especificar la ruta de acceso del archivo. Para establecer la ruta de acceso del directorio de inclusión en Visual Studio, abra el proyecto **páginas de propiedades** cuadro de diálogo, expanda **Propiedades de configuración** y **directorios de VC ++**, y, a continuación, edite el **directorios de inclusión** valor. Para obtener más información acerca de los directorios de CAL por usuario y por proyecto realiza la búsqueda del compilador en Visual Studio, vea [página de propiedades de directorios de VC ++](../../ide/vcpp-directories-property-page.md). Para obtener más información sobre la **/I** opción del compilador, vea [/I (directorios de inclusión adicionales)](../../build/reference/i-additional-include-directories.md).  
  
 **Se incluye una versión incorrecta de un nombre de archivo**  
  
 Un error C1083 también puede indicar que la versión incorrecta de un archivo está incluida. Por ejemplo, una compilación podría incluir la versión incorrecta de un archivo que tiene una directiva `include` para un archivo de encabezado que no está previsto para esa compilación. Cuando el archivo de encabezado no se encuentra, el compilador genera un error C1083. La corrección para este problema es utilizar el archivo correcto y no agregar el archivo de encabezado o directorio a la compilación.  
  
 **Los encabezados precompilados aún no se precompilan**  
  
 Cuando se configura un proyecto para usar encabezados precompilados, los archivos pertinentes .pch se tienen que crear para que los archivos que utilizan el contenido del encabezado puedan compilarse. Por ejemplo, el archivo de stdafx.cpp se crea automáticamente en el directorio de proyecto para los nuevos proyectos de MFC. Se compila primero el archivo para crear archivos de encabezado precompilados. (En el diseño del proceso de compilación normal, esto se hace automáticamente.) Para obtener más información, vea [crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md).  
  
 **Otras causas**  
  
-   El archivo usa código administrado, pero la opción del compilador **/CLR** no se ha especificado. Para obtener más información, vea [/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
-   El archivo se compila mediante un diferentes **/ analyze** valor de la opción de compilador que se usa para precompilar los encabezados. (Cuando los encabezados para un proyecto se precompilan, todos deben usar la misma **/ analyze** configuración.) Para obtener más información, vea [/analyze (análisis de código)](../../build/reference/analyze-code-analysis.md).  
  
-   El archivo, el directorio o el disco es de solo lectura.  
  
-   No se conceden los permisos de acceso del archivo o directorio.  
  
-   No hay suficientes identificadores de archivo. Cierre algunas aplicaciones y, a continuación, compile de nuevo. Esta condición es poco habitual en circunstancias normales. Sin embargo, puede aparecer cuando se compilan proyectos grandes en un equipo con memoria física limitada.  
  
 En el ejemplo siguiente se genera un error C1083.  
  
```  
// C1083.cpp  
// compile with: /c  
#include "test.h"   // C1083 test.h does not exist  
#include "stdio.h"   // OK  
```  
  
 Para obtener información sobre cómo compilar proyectos de C o C++ en el IDE o en la línea de comandos e información acerca de cómo establecer variables de entorno, consulte [compilar programas de C o C++](../../build/building-c-cpp-programs.md).
 
 ## <a name="see-also"></a>Vea también
 [Propiedades de MSBuild](MSBuild%20Properties.md)