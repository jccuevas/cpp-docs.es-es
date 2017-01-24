---
title: "/Od (Deshabilitar (Depurar)) | Microsoft Docs"
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
  - "/od"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Od (opción del compilador) [C++]"
  - "deshabilitar (depurar): opción del compilador [C++]"
  - "deshabilitar optimizaciones"
  - "compilación rápida"
  - "sin optimizaciones"
  - "Od (opción del compilador) [C++]"
  - "-Od (opción del compilador) [C++]"
ms.assetid: b1ac31b7-e086-4eeb-be5e-488f7513f5f5
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Od (Deshabilitar (Depurar))
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Desactiva todas las optimizaciones en el programa y acelera la compilación.  
  
## Sintaxis  
  
```  
/Od  
```  
  
## Comentarios  
 Es la opción predeterminada.  Dado que **\/Od** suprime el movimiento del código, simplifica el proceso de depuración.  Para obtener más información sobre las opciones del compilador para la depuración, vea [\/Z7, \/Zi, \/ZI \(Formato de la información de depuración\)](../../build/reference/z7-zi-zi-debug-information-format.md).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Optimización**.  
  
4.  Modifique la propiedad **Optimización**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.  
  
## Vea también  
 [\/O \(Opciones\) \(Optimizar código\)](../../build/reference/o-options-optimize-code.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [\/Z7, \/Zi, \/ZI \(Formato de la información de depuración\)](../../build/reference/z7-zi-zi-debug-information-format.md)