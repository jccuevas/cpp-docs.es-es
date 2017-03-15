---
title: "/Fo (Nombre del archivo objeto) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/Fo"
  - "VC.Project.VCCLCompilerTool.ObjectFile"
  - "VC.Project.VCCLWCECompilerTool.ObjectFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Fo (opción del compilador) [C++]"
  - "Fo (opción del compilador) [C++]"
  - "-Fo (opción del compilador) [C++]"
  - "archivos objeto, asignar nombre"
ms.assetid: 0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /Fo (Nombre del archivo objeto)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica un nombre de archivo objeto \(.obj\) o un directorio que debe utilizarse en lugar del valor predeterminado.  
  
## Sintaxis  
  
```  
/Fopathname  
```  
  
## Comentarios  
 Si no usa esta opción, el archivo objeto utiliza el nombre base del archivo de código fuente y la extensión .obj.  Puede usar cualquier nombre y extensión que desee, aunque se recomienda utilizar .obj.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Archivos de resultados**.  
  
4.  Modifique la propiedad **Nombre de archivo objeto**.  En el entorno de desarrollo, el archivo objeto debe tener una extensión .obj.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ObjectFile%2A>.  
  
## Ejemplo  
 La línea de comandos siguiente crea un archivo objeto denominado THIS.obj en un directorio ya existente, \\OBJECT, de la unidad B.  
  
```  
CL /FoB:\OBJECT\ THIS.C  
```  
  
## Vea también  
 [\/F \(Opciones del archivo de resultados\)](../../build/reference/output-file-f-options.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [Especificar la ruta de acceso](../../build/reference/specifying-the-pathname.md)