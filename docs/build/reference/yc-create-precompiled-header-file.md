---
title: "/Yc (Crear archivo de encabezado precompilado) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.UsePrecompiledHeader"
  - "/yc"
  - "VC.Project.VCCLWCECompilerTool.PrecompiledHeaderThrough"
  - "VC.Project.VCCLWCECompilerTool.UsePrecompiledHeader"
  - "VC.Project.VCCLCompilerTool.PrecompiledHeaderThrough"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pch (archivos), crear"
  - "/Yc (opción del compilador) [C++]"
  - "PCH (archivos), crear"
  - "archivos de encabezado precompilados, crear"
  - "Yc (opción del compilador) [C++]"
  - "-Yc (opción del compilador) [C++]"
ms.assetid: 47c2e555-b4f5-46e6-906e-ab5cf21f0678
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /Yc (Crear archivo de encabezado precompilado)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Indica al compilador que cree un archivo de encabezado precompilado \(.pch\) que represente el estado de compilación en un punto determinado.  
  
## Sintaxis  
  
```  
/Yc[filename]  
```  
  
## Argumentos  
 `filename`  
 Especifica un archivo de encabezado \(.h\).  Cuando se utiliza este argumento, el compilador compila todo el código hasta el archivo .h, incluido.  
  
## Comentarios  
 Si se especifica **\/Yc** sin ningún argumento, el compilador compila todo el código hasta el final del archivo base de código fuente o hasta el punto del archivo base en el que aparece un [hdrstop](../../preprocessor/hdrstop.md).  El archivo .pch resultante tiene el mismo nombre base que el archivo base de código fuente, a menos que se especifique otro nombre mediante el pragma **hdrstop** o la opción **\/Fp**.  
  
 El código precompilado se guarda en un archivo con un nombre creado a partir del nombre base del archivo especificado con la opción **\/Yc** y una extensión .pch.  También se puede utilizar la opción [\/Fp \(Dar nombre al archivo .Pch\)](../../build/reference/fp-name-dot-pch-file.md) para especificar el nombre del archivo de encabezado precompilado.  
  
 Si utiliza **\/Yc**`filename`, el compilador compila todo el código hasta el archivo especificado \(incluido\), para uso subsiguiente con la opción **\/Yu**.  
  
 Si las opciones **\/Yc**`filename` y [\/Yu \(Utilizar el archivo de encabezado precompilado\)](../../build/reference/yu-use-precompiled-header-file.md)`filename` aparecen en la misma línea de comandos y ambas hacen referencia o implican al mismo nombre de archivo, **\/Yc**`filename` tiene prioridad.  Esta característica simplifica la creación de archivos MAKE.  
  
 Para obtener más información acerca de los encabezados precompilados, vea:  
  
-   [\/Y \(Encabezados precompilados\)](../../build/reference/y-precompiled-headers.md)  
  
-   [Crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md)  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Seleccione un archivo .cpp.  El archivo .cpp debe utilizar \#include con el archivo .h que contiene la información de encabezado precompilada.  El valor de **\/Yc** del proyecto se puede reemplazar en el nivel del archivo.  
  
2.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
3.  Haga clic en la carpeta **C\/C\+\+**.  
  
4.  Haga clic en la página de propiedades **Encabezados precompilados**.  
  
5.  Modifique la propiedad **Crear o usar PCH a través de archivo** o **Crear o utilizar encabezado precompilado**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>.  
  
## Ejemplo  
 Observe el código siguiente:  
  
```  
#include <afxwin.h>   // Include header for class library  
#include "resource.h" // Include resource definitions  
#include "myapp.h"    // Include information specific to this app  
...  
```  
  
 Cuando este código se compila con el comando `CL /YcMYAPP.H PROG.CPP`, el compilador guarda todo el preprocesamiento correspondiente a AFXWIN.h, RESOURCE.h y MYAPP.h en un archivo de encabezado precompilado denominado MYAPP.pch.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)