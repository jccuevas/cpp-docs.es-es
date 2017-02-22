---
title: "/FI (Dar nombre al archivo de inclusi&#243;n obligatorio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCNMakeTool.ForcedIncludes"
  - "VC.Project.VCCLCompilerTool.ForcedIncludeFiles"
  - "VC.Project.VCCLWCECompilerTool.ForcedIncludeFiles"
  - "/fi"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/FI (opción del compilador) [C++]"
  - "FI (opción del compilador) [C++]"
  - "-FI (opción del compilador) [C++]"
  - "preprocesar archivo de encabezado (opción del compilador) [C++]"
ms.assetid: 07e79577-8152-4df9-a64c-aae08c603397
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /FI (Dar nombre al archivo de inclusi&#243;n obligatorio)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Hace que el preprocesador procese el archivo de encabezado especificado.  
  
## Sintaxis  
  
```  
/FI[ ]pathname  
```  
  
## Comentarios  
 Tiene el mismo efecto que especificar el archivo con comillas dobles en una directiva `#include` en la primera línea de todos los archivos de código fuente especificados en la línea de comandos, en la variable de entorno CL o en un archivo de comandos.  Si usa varias opciones **\/FI**, los archivos se incluyen en el orden en que los procesa CL.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Avanzadas**.  
  
4.  Modifique la propiedad **Forzar inclusiones**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedIncludeFiles%2A>.  
  
## Vea también  
 [\/F \(Opciones del archivo de resultados\)](../../build/reference/output-file-f-options.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Especificar la ruta de acceso](../../build/reference/specifying-the-pathname.md)