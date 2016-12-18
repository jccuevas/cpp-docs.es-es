---
title: "/Qsafe_fp_loads | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 2b2ce52d-ba57-4bd3-a739-47a7f8bfaba9
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Qsafe_fp_loads
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Requiere instrucciones de movimiento de enteros para los valores de punto flotante y deshabilita ciertas optimizaciones de carga de punto flotante.  
  
## Sintaxis  
  
```  
/Qsafe_fp_loads  
```  
  
## Comentarios  
 **\/Qsafe\_fp\_loads** solo está disponible en los compiladores destinados a x86; no está disponible en los compiladores destinados a x64 o ARM.  
  
 **\/Qsafe\_fp\_loads** fuerza que el compilador utilice instrucciones de movimiento de enteros en lugar de instrucciones de movimiento de punto flotante para mover datos entre la memoria y los registros MMX.  Esta opción también deshabilita la optimización de la carga del Registro para los valores de punto flotante que se pueden cargar en varias rutas cuando el valor puede producir una excepción en la carga, por ejemplo, un valor NaN.  
  
 Esta opción se invalida con [\/fp:except](../../build/reference/fp-specify-floating-point-behavior.md).  **\/Qsafe\_fp\_loads** especifica un subconjunto del comportamiento del compilador especificado por **\/fp:except**.  
  
 **\/Qsafe\_fp\_loads** es incompatible con [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) y [\/fp:fast](../../build/reference/fp-specify-floating-point-behavior.md).  Para obtener más información sobre las opciones del compilador de punto flotante, vea [\/fp \(Especificar comportamiento de punto flotante\)](../../build/reference/fp-specify-floating-point-behavior.md).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Seleccione la carpeta **C\/C\+\+**.  
  
3.  Seleccione la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [\/Q \(Opciones\) \(Operaciones de bajo nivel\)](../../build/reference/q-options-low-level-operations.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)