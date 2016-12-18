---
title: "/C (Conservar los comentarios durante el preprocesamiento) | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.KeepComments"
  - "/c"
  - "VC.Project.VCCLWCECompilerTool.KeepComments"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/c (opción del compilador) [C++]"
  - "c (opción del compilador) [C++]"
  - "-c (opción del compilador) [C++]"
  - "comentarios, no eliminar durante el preprocesamiento"
  - "conservar los comentarios durante el preprocesamiento"
ms.assetid: 944567ca-16bc-4728-befe-d414a7787f26
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /C (Conservar los comentarios durante el preprocesamiento)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Conserva los comentarios durante el preprocesamiento  
  
## Sintaxis  
  
```  
/C  
```  
  
## Comentarios  
 Esta opción del compilador requiere la opción **\/E**, **\/P** o **\/EP**.  
  
 En el ejemplo de código siguiente se muestra el comentario sobre el código fuente.  
  
```  
// C_compiler_option.cpp  
// compile with: /E /C /c  
int i;   // a variable  
```  
  
 Este ejemplo genera el siguiente resultado.  
  
```  
#line 1 "C_compiler_option.cpp"  
int i;   // a variable  
```  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Preprocesador**.  
  
4.  Modifique la propiedad **Mantener comentarios**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.KeepComments%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [\/E \(Preprocesar para stdout\)](../../build/reference/e-preprocess-to-stdout.md)   
 [\/P \(Preprocesar y escribir en un archivo\)](../../build/reference/p-preprocess-to-a-file.md)   
 [\/EP \(Preprocesar para stdout sin directivas \#line\)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)