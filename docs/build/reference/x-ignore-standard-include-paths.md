---
title: "/X (Omitir rutas de acceso de inclusi&#243;n est&#225;ndar) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/x"
  - "VC.Project.VCCLCompilerTool.IgnoreStandardIncludePath"
  - "VC.Project.VCCLWCECompilerTool.IgnoreStandardIncludePath"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/X (opción del compilador) [C++]"
  - "omitir rutas de acceso de inclusión estándar (opción del compilador)"
  - "directorios de inclusión, omitir estándar"
  - "archivos de inclusión, omitir la ruta de acceso estándar"
  - "X (opción del compilador)"
  - "-X (opción del compilador) [C++]"
ms.assetid: 16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# /X (Omitir rutas de acceso de inclusi&#243;n est&#225;ndar)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Impide que el compilador busque archivos de inclusión en los directorios especificados en las variables de entorno PATH e INCLUDE.  
  
## Sintaxis  
  
```  
/X  
```  
  
## Comentarios  
 No se puede utilizar esta opción con la opción [\/I \(Directorios de inclusión adicionales\)](../../build/reference/i-additional-include-directories.md) \(**\/I**`directory`\).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Preprocesador**.  
  
4.  Modifique la propiedad **Omitir ruta de acceso de inclusión estándar**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.IgnoreStandardIncludePath%2A>.  
  
## Ejemplo  
 En el comando siguiente, `/X` indica al compilador que no tenga en cuenta las ubicaciones especificadas por las variables de entorno PATH e INCLUDE, e `/I` especifica el directorio donde se deben buscar los archivos de inclusión:  
  
```  
CL /X /I \ALT\INCLUDE MAIN.C  
```  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)