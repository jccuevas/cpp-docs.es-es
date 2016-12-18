---
title: "/AI (Especificar directorios de metadatos) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.AdditionalUsingDirectories"
  - "VC.Project.VCNMakeTool.AssemblySearchPath"
  - "/AI"
  - "VC.Project.VCCLWCECompilerTool.AdditionalUsingDirectories"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/AI (opción del compilador) [C++]"
  - "AI (opción del compilador) [C++]"
  - "-AI (opción del compilador) [C++]"
ms.assetid: fb9c1846-504c-4a3b-bb39-c8696de32f6f
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /AI (Especificar directorios de metadatos)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica un directorio en el que el compilador debe buscar para resolver las referencias de archivos que se pasan a la directiva `#using`.  
  
## Sintaxis  
  
```  
/AIdirectory  
```  
  
## Argumentos  
 `directory`  
 Directorio o ruta de acceso donde debe buscar el compilador.  
  
## Comentarios  
 Solo se puede pasar un directorio a una invocación de **\/AI**.  Especifique una opción **\/AI** para cada ruta de acceso en la que desea que busque el compilador.  Por ejemplo, para agregar C:\\Project\\Meta y C:\\Common\\Meta a la ruta de búsqueda del compilador en las directivas `#using`, agregue `/AI"C:\Project\Meta" /AI"C:\Common\Meta"` a la línea de comandos del compilador o agregue cada directorio a la propiedad **Directorios \#using adicionales** de Visual Studio.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  En el panel de navegación, seleccione **Propiedades de configuración**, **C\/C\+\+** y **General**.  
  
3.  Modifique la propiedad **Directorios \#using adicionales**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalUsingDirectories%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [\#using \(Directiva\)](../../preprocessor/hash-using-directive-cpp.md)