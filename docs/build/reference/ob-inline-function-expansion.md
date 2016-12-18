---
title: "/Ob (Expansi&#243;n de funciones inline) | Microsoft Docs"
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
  - "VC.Project.VCCLWCECompilerTool.InlineFunctionExpansion"
  - "VC.Project.VCCLCompilerTool.InlineFunctionExpansion"
  - "/ob"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Ob (opción del compilador) [C++]"
  - "/Ob0 (opción del compilador) [C++]"
  - "/Ob1 (opción del compilador) [C++]"
  - "/Ob2 (opción del compilador) [C++]"
  - "cualquiera adecuado (opción del compilador) [C++]"
  - "disable (opción del compilador) [C++]"
  - "expansión en línea, opción del compilador"
  - "funciones inline, expansión de funciones (opción del compilador) [C++]"
  - "Ob (opción del compilador) [C++]"
  - "-Ob (opción del compilador) [C++]"
  - "Ob0 (opción del compilador) [C++]"
  - "-Ob0 (opción del compilador) [C++]"
  - "Ob1 (opción del compilador) [C++]"
  - "-Ob1 (opción del compilador) [C++]"
  - "Ob2 (opción del compilador) [C++]"
  - "-Ob2 (opción del compilador) [C++]"
  - "only __inline (opción del compilador) [C++]"
ms.assetid: f134e6df-e939-4980-a01d-47425dbc562a
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Ob (Expansi&#243;n de funciones inline)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Controla la expansión en línea de las funciones.  
  
## Sintaxis  
  
```  
/Ob{0|1|2}  
```  
  
## Argumentos  
 **0**  
 Deshabilita las expansiones en línea.  De forma predeterminada, la expansión se produce a discreción del compilador en todas las funciones, normalmente conocido como *inline automático*.  
  
 **1**  
 Permite la expansión solo de las funciones marcadas como [inline](../../misc/inline-inline-forceinline.md), [\_\_inline](../../misc/inline-inline-forceinline.md) o [\_\_forceinline](../../misc/inline-inline-forceinline.md), o en una función miembro de C\+\+ definida en una declaración de clase.  
  
 **2**  
 Valor predeterminado.  Permite la expansión de las funciones marcadas como `inline`, `__inline` o `__forceinline` y de cualquier otra función que elija el compilador.  
  
 **\/Ob2** se habilita cuando se usa [\/O1, \/O2 \(Minimizar tamaño, maximizar velocidad\)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) o [\/Ox \(Optimización completa\)](../../build/reference/ox-full-optimization.md).  
  
 Esta opción requiere que habilite las optimizaciones mediante **\/O1**, **\/O2**, **\/Ox** o **\/Og**.  
  
## Comentarios  
 El compilador trata las opciones de expansión insertada y las palabras clave como sugerencias.  No hay ninguna garantía de que las funciones es expandan en línea.  Puede deshabilitar las expansiones en línea, pero no se puede forzar al compilador a que inserte una función determinada, incluso cuando se usa la palabra clave `__forceinline`.  
  
 Puede usar la directiva `#pragma` [auto\_inline](../../preprocessor/auto-inline.md) para excluir funciones de la consideración, como candidatos para la expansión en línea.  Consulte también la directiva `#pragma` [intrinsic](../../preprocessor/intrinsic.md).  
  
> [!NOTE]
>  La información que se recopila a partir de las pruebas de generación de perfiles reemplazará las optimizaciones que, en caso contrario, estarían activas si se especificara **\/Ob**, **\/Os** o **\/Ot**.  Para obtener más información, consulte [Optimizaciones guiadas por perfiles](../../build/reference/profile-guided-optimizations.md).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, consulte [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Expanda **Propiedades de configuración**, **C o C\+\+** y seleccione **Optimización**.  
  
3.  Modifique la propiedad **Expansión de funciones en línea**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.InlineFunctionExpansion%2A>.  
  
## Vea también  
 [\/O \(Opciones\) \(Optimizar código\)](../../build/reference/o-options-optimize-code.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)