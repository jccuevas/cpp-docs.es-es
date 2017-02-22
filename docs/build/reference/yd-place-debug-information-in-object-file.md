---
title: "/Yd (Incluir informaci&#243;n de depuraci&#243;n en un archivo objeto) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/yd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Yd (opción del compilador) [C++]"
  - "depurar [C++], archivos de información de depuración"
  - "Yd (opción del compilador) [C++]"
  - "-Yd (opción del compilador) [C++]"
ms.assetid: c5a699fe-65ce-461e-964c-7f5eb2a8320a
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# /Yd (Incluir informaci&#243;n de depuraci&#243;n en un archivo objeto)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Incluye la información de depuración completa en todos los archivos objeto creados a partir de un archivo de encabezado precompilado \(.pch\) cuando se utiliza con las opciones [\/Yc](../../build/reference/yc-create-precompiled-header-file.md) y [\/Z7](../../build/reference/z7-zi-zi-debug-information-format.md).  Obsoleto.  
  
## Sintaxis  
  
```  
/Yd  
```  
  
## Comentarios  
 **\/Yd** está desusado; ahora [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] admite que varios objetos escriban en un archivo .pdb único; use **\/Zi** en su lugar.  Para obtener más información, vea [Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/es-es/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce).  
  
 A menos que necesite distribuir una biblioteca que contiene información de depuración, utilice la opción [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) en lugar de **\/Z7** y **\/Yd**.  
  
 El almacenamiento de la información de depuración completa en todos los archivos .obj sólo es necesario para distribuir bibliotecas que contienen información de depuración.  Su compilación es más lenta y requiere un espacio en el disco considerable.  Si se utiliza **\/Yc** y **\/Z7** sin **\/Yd**, el compilador almacena la información de depuración común en el primer archivo .obj creado a partir del archivo .pch.  El compilador no inserta esta información en los archivos .obj creados con posterioridad a partir del archivo .pch, sino que inserta referencias cruzadas a la información.  Con independencia del número de archivos .obj que use el archivo .pch, solamente uno de ellos contiene la información de depuración común.  
  
 Aunque este comportamiento predeterminado logra tiempos de compilación mucho más cortos y reduce las demandas de espacio en el disco, no es conveniente si un cambio pequeño requiere recompilar el archivo .obj que contiene la información de depuración común.  En este caso, el compilador debe recompilar todos los archivos .obj que contengan referencias cruzadas al archivo .obj original.  Asimismo, si proyectos diferentes utilizan un archivo .pch común, confiar las referencias cruzadas a un solo archivo .obj es difícil.  
  
 Para obtener más información acerca de los encabezados precompilados, vea:  
  
-   [\/Y \(Encabezados precompilados\)](../../build/reference/y-precompiled-headers.md)  
  
-   [Crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md)  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Ejemplos  
 Supongamos que cuenta con dos archivos base, F.cpp y G.cpp, cada uno de los cuales contiene estas instrucciones **\#include**:  
  
```  
#include "windows.h"  
#include "etc.h"  
```  
  
 El comando siguiente crea el archivo de encabezado precompilado ETC.pch y el archivo objeto F.obj:  
  
```  
CL /YcETC.H /Z7 F.CPP  
```  
  
 El archivo objeto F.obj incluye información de tipos y símbolos para WINDOWS.h y ETC.h \(y cualquier otro archivo de encabezado que incluya\).  Ahora puede usar el encabezado precompilado ETC.pch para compilar el archivo de código fuente G.cpp:  
  
```  
CL /YuETC.H /Z7 G.CPP  
```  
  
 El archivo objeto G.obj no incluye la información de depuración correspondiente al encabezado precompilado, sino sencillamente referencias a dicha información en el archivo F.obj.  Tenga en cuenta que debe crear un vínculo con el archivo F.obj.  
  
 Si el encabezado precompilado no fue compilado con **\/Z7**, sigue siendo posible usarlo en compilaciones posteriores con **\/Z7**.  No obstante, la información de depuración se coloca en el archivo objeto actual, pero los símbolos locales de funciones y tipos definidos en el encabezado precompilado no estarán disponibles para el depurador.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)