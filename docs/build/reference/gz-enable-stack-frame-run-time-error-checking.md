---
title: "/GZ (Habilitar comprobaci&#243;n de errores del marco de pila en tiempo de ejecuci&#243;n) | Microsoft Docs"
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
  - "/gz"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/GZ (opción del compilador) [C++]"
  - "compilaciones de depuración, interceptar errores de versión de lanzamiento"
  - "GZ (opción del compilador) [C++]"
  - "-GZ (opción del compilador) [C++]"
  - "errores de versión de lanzamiento"
ms.assetid: b3efeeff-d5e3-4057-91c9-f6fc73d0270c
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /GZ (Habilitar comprobaci&#243;n de errores del marco de pila en tiempo de ejecuci&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Realiza las mismas operaciones que la opción [\/RTC \(Comprobaciones de errores en tiempo de ejecución\)](../../build/reference/rtc-run-time-error-checks.md).  Obsoleto.  
  
## Sintaxis  
  
```  
/GZ  
```  
  
## Comentarios  
 **\/GZ** es solo para uso en una compilación \([\/Od \(Deshabilitar \(Depurar\)\)](../../build/reference/od-disable-debug.md)\) no optimizada.  
  
 **\/GZ** está desusado; utilice [\/RTC \(Comprobaciones de errores en tiempo de ejecución\)](../../build/reference/rtc-run-time-error-checks.md) en su lugar.  Para obtener más información, vea [Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/es-es/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce).  
  
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