---
title: "/Ge (Habilitar comprobaciones de la pila) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/ge"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Ge (opción del compilador) [C++]"
  - "habilitar comprobaciones de la pila"
  - "Ge (opción del compilador) [C++]"
  - "-Ge (opción del compilador) [C++]"
  - "llamadas de comprobación de la pila"
  - "comprobaciones de la pila"
  - "pila, comprobaciones de la pila"
ms.assetid: 4b54deae-4e3c-4bfa-95f3-ba23590f7258
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# /Ge (Habilitar comprobaciones de la pila)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Activa las comprobaciones de la pila por cada llamada de función que requiere almacenamiento de variables locales.  
  
## Sintaxis  
  
```  
/Ge  
```  
  
## Comentarios  
 Este mecanismo es útil para volver a escribir la funcionalidad de la comprobación de la pila.  Se recomienda utilizar el método [\/GH \(Habilitar la función de enlace \_penter\)](../../build/reference/gh-enable-penter-hook-function.md) en lugar de volver a escribir la comprobación de la pila.  
  
 [\/Gs \(Controlar llamadas de comprobación de la pila\)](../../build/reference/gs-control-stack-checking-calls.md) produce el mismo efecto.  
  
 La opción **\/Ge** ha quedado desusada; el compilador generará la comprobación de la pila.  Para obtener más información, vea [Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/es-es/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)