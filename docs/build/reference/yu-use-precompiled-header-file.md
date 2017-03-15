---
title: "/Yu (Utilizar el archivo de encabezado precompilado) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/yu"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pch (archivos), usar existente"
  - "/Yu (opción del compilador) [C++]"
  - "PCH (archivos), usar existente"
  - "archivos de encabezado precompilados, usar existente"
  - "Yu (opción del compilador) [C++]"
  - "-Yu (opción del compilador) [C++]"
ms.assetid: 24f1bd0e-b624-4296-a17e-d4b53e374e1f
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /Yu (Utilizar el archivo de encabezado precompilado)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Indica al compilador que use un archivo de encabezado precompilado existente \(.pch\) en la compilación actual.  
  
## Sintaxis  
  
```  
/Yu[filename]  
```  
  
## Argumentos  
 *filename*  
 El nombre de un archivo de encabezado, que se incluye en el archivo de código fuente mediante una directiva de preprocesador **\#include**.  
  
## Comentarios  
 El nombre del archivo de inclusión debe ser el mismo tanto para la opción **\/Yc** que crea el encabezado precompilado como para cualquier opción **\/Yu** posterior que indique el uso del encabezado precompilado.  
  
 Para **\/Yc**, `filename` especifica el punto en el que se detiene la precompilación; el compilador precompila todo el código hasta `filename` y asigna al encabezado precompilado resultante un nombre compuesto por el nombre base del archivo de inclusión y la extensión .pch.  
  
 El archivo .pch se debe haber creado mediante **\/Yc**.  
  
 El compilador trata todo el código existente antes del archivo .h como precompilado.  Pasa por alto hasta justo después de la directiva **\#include** asociada al archivo .h, usa el código que contiene el archivo .pch y luego compila todo el código siguiente a `filename`.  
  
 En la línea de comandos, no se permiten espacios entre **\/Yu** y `filename`.  
  
 Si se especifica la opción **\/Yu** sin un nombre de archivo, el programa fuente debe contener un [\#pragma hdrstop](../../preprocessor/hdrstop.md) que especifique el nombre del archivo de encabezado precompilado \(.pch\).  En este caso, el compilador utilizará el encabezado precompilado \(archivo .pch\) especificado mediante [\/Fp \(Dar nombre al archivo .Pch\)](../../build/reference/fp-name-dot-pch-file.md).  El compilador salta hasta la ubicación del pragma, restaura el estado compilado del archivo de encabezado precompilado especificado por el pragma y compila solamente el código siguiente al pragma.  Si **\#pragma hdrstop** no especifica un nombre de archivo, el compilador busca un archivo con un nombre derivado del nombre base del archivo de código fuente y la extensión .pch.  También puede usar la opción **\/Fp** para especificar otro archivo .pch.  
  
 Si especifica la opción **\/Yu** sin un nombre de archivo pero no especifica un pragma **hdrstop**, se genera un mensaje de error y la compilación no se realiza correctamente.  
  
 Si las opciones **\/Yc**`filename` y  **\/Yu**`filename` aparecen en la misma línea de comandos y ambas hacen referencia al mismo nombre de archivo, **\/Yc**`filename` tiene prioridad y precompila todo el código, hasta el archivo con nombre incluido.  Esta característica simplifica la creación de archivos MAKE.  
  
 Dado que los archivos .pch contienen información sobre el entorno del equipo, así como datos de direcciones de memoria del programa, un archivo .pch sólo se debe utilizar en el equipo en el que se creó.  
  
 Para obtener más información acerca de los encabezados precompilados, vea:  
  
-   [\/Y \(Encabezados precompilados\)](../../build/reference/y-precompiled-headers.md)  
  
-   [Crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md)  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Especifique [\/Yc \(Crear archivo de encabezado precompilado\)](../../build/reference/yc-create-precompiled-header-file.md) en un archivo .cpp de su proyecto.  
  
2.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
3.  Haga clic en la carpeta **C\/C\+\+**.  
  
4.  Haga clic en la página de propiedades **Encabezados precompilados**.  
  
5.  Modifique la propiedad **Crear o usar PCH a través de archivo** o **Crear o utilizar encabezado precompilado**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>.  
  
## Ejemplos  
 Si el código siguiente:  
  
```  
#include <afxwin.h>   // Include header for class library  
#include "resource.h" // Include resource definitions  
#include "myapp.h"    // Include information specific to this app  
...  
```  
  
 se compila con la línea de comandos `CL /YuMYAPP.H PROG.CPP`, el compilador no procesa las tres instrucciones include, sino que usa el código precompilado de MYAPP.pch, lo que ahorra el tiempo invertido en el preprocesamiento de los tres archivos \(y de cualquier archivo que puedan incluir\).  
  
 Puede utilizar la opción [\/Fp \(Dar nombre al archivo .Pch\)](../../build/reference/fp-name-dot-pch-file.md) con **\/Yu** para especificar el nombre del archivo .pch, si éste es distinto del argumento de nombre de archivo de **\/Yc** o del nombre base del archivo de código fuente, como se indica a continuación:  
  
```  
CL /YuMYAPP.H /FpMYPCH.pch PROG.CPP  
```  
  
 Este comando especifica un archivo de encabezado precompilado denominado MYPCH.pch.  El compilador utiliza su contenido para restaurar el estado precompilado de todos los archivos de encabezado hasta MYAPP.h \(incluido\).  El compilador compila entonces el código que aparece después de la instrucción **include** de MYAPP.h.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)