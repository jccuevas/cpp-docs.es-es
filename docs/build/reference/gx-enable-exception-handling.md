---
title: "/GX (Habilitar el control de excepciones) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/gx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/GX (opción del compilador) [C++]"
  - "cl.exe (compilador), control de excepciones"
  - "habilitar el control de excepciones (opción del compilador) [C++]"
  - "control de excepciones, habilitar"
  - "GX (opción del compilador) [C++]"
  - "-GX (opción del compilador) [C++]"
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# /GX (Habilitar el control de excepciones)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Habilita el control sincrónico de excepciones bajo el supuesto de que las funciones `extern` de C nunca producen una excepción.  
  
## Sintaxis  
  
```  
/GX  
```  
  
## Comentarios  
 Equivale a [\/EH \(Modelo de control de excepciones\)](../../build/reference/eh-exception-handling-model.md).  
  
 **\/GX** se activa, de manera predeterminada, cuando se compila desde el entorno de desarrollo.  De forma predeterminada, **\/GX\-** está habilitada cuando se utilizan herramientas de la línea de comandos.  
  
 Para obtener más información, vea [Control de excepciones de C\+\+](../../cpp/cpp-exception-handling.md).  
  
 **\/GX** está desusado; utilice [\/EH \(Modelo de control de excepciones\)](../../build/reference/eh-exception-handling-model.md) en su lugar.  Para obtener más información, vea [Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/es-es/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce).  
  
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