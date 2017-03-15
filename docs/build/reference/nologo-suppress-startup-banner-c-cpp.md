---
title: "/NOLOGO (Suprimir el titular de inicio) (C/C++) | Microsoft Docs"
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
  - "VC.Project.VCCLWCECompilerTool.SuppressStartupBanner"
  - "VC.Project.VCCLCompilerTool.SuppressStartupBanner"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/nologo (opción del compilador) [C++]"
  - "titulares, suprimir inicio"
  - "nologo (opción del compilador) [C++]"
  - "-nologo (opción del compilador) [C++]"
ms.assetid: 75930d8b-b11c-4db8-99e5-b52f97da0693
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /NOLOGO (Suprimir el titular de inicio) (C/C++)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Suprime la presentación del aviso de copyright cuando se ejecuta el compilador y la de los mensajes de información durante la compilación.  
  
## Sintaxis  
  
```  
/nologo  
```  
  
## Comentarios  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **General**.  
  
4.  Modifique la propiedad **Suprimir la pancarta de inicio**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SuppressStartupBanner%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)