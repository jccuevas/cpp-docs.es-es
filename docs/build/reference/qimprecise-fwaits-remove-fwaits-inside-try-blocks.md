---
title: "/Qimprecise_fwaits (Quitar comandos fwait en los bloques Try) | Microsoft Docs"
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
  - "/Qimprecise_fwaits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Qimprecise_fwaits (opción del compilador) (C++)"
  - "-Qimprecise_fwaits (opción del compilador) (C++)"
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Qimprecise_fwaits (Quitar comandos fwait en los bloques Try)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Quita los comandos `fwait` internos de los bloques `try` cuando se utiliza la opción del compilador [\/fp:except](../../build/reference/fp-specify-floating-point-behavior.md).  
  
## Sintaxis  
  
```  
/Qimprecise_fwaits  
```  
  
## Comentarios  
 Esta opción no tiene ningún efecto si no se especifica también **\/fp:except**.  Si especifica la opción **\/fp:except**, el compilador insertará un comando `fwait` alrededor de cada línea de código de un bloque `try`.  De esta forma, el compilador puede identificar la línea de código específica que genera una excepción.  **\/Qimprecise\_fwaits** quita las instrucciones `fwait` internas y solo deja las instrucciones wait alrededor del bloque `try`.  De esta forma, mejorará el rendimiento, pero el compilador sólo podrá indicar en qué bloque `try` se produce una excepción, no en qué línea.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [\/Q \(Opciones\) \(Operaciones de bajo nivel\)](../../build/reference/q-options-low-level-operations.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)