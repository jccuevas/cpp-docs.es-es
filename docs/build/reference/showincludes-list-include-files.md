---
title: "/showIncludes (Enumerar archivos de inclusi&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLWCECompilerTool.ShowIncludes"
  - "VC.Project.VCCLCompilerTool.ShowIncludes"
  - "/showincludes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/showIncludes (opción del compilador) [C++]"
  - "archivos de inclusión"
  - "archivos de inclusión, mostrar en la compilación"
  - "showIncludes (opción del compilador) [C++]"
  - "-showIncludes (opción del compilador) [C++]"
ms.assetid: 0b74b052-f594-45a6-a7c7-09e1a319547d
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /showIncludes (Enumerar archivos de inclusi&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Hace que el compilador genere una lista de los archivos de inclusión.  También se muestran los archivos de inclusión anidados \(archivos que se incluyen a partir de los archivos incluidos\).  
  
## Sintaxis  
  
```  
/showIncludes  
```  
  
## Comentarios  
 Si se encuentra un archivo de inclusión durante la compilación, se emite un mensaje, por ejemplo:  
  
```  
Note: including file: d:\MyDir\include\stdio.h  
```  
  
 Los archivos de inclusión anidados se indican mediante una sangría, de un espacio por cada nivel de anidación, por ejemplo:  
  
```  
Note: including file: d:\temp\1.h  
Note: including file:  d:\temp\2.h  
```  
  
 En este caso, el archivo `2.h` se ha incluido desde el archivo `1.h`, de ahí la sangría.  
  
 La opción **\/showIncludes** emite a `stderr`, no a `stdout`.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Avanzadas**.  
  
4.  Modifique la propiedad **Mostrar inclusiones**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ShowIncludes%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)