---
title: "/Oy (Omisi&#243;n de puntero de marco) | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.OmitFramePointers"
  - "/oy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Oy (opción del compilador) [C++]"
  - "omisión de puntero a marco (opción del compilador) [C++]"
  - "omitir puntero a marco"
  - "Oy (opción del compilador) [C++]"
  - "-Oy (opción del compilador) [C++]"
  - "puntero a marco de pila (opción del compilador) [C++]"
  - "suprimir la creación de punteros a marcos"
ms.assetid: c451da86-5297-4c5a-92bc-561d41379853
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Oy (Omisi&#243;n de puntero de marco)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Suprime la creación de punteros de marcos en la pila de llamadas.  
  
## Sintaxis  
  
```  
/Oy[-]  
```  
  
## Comentarios  
 Esta opción acelera las llamadas de función, ya que no es necesario configurar y quitar punteros de marco.  También libera un registro más \(EBP en Intel 386 o posterior\) para almacenar variables y subexpresiones que se utilizan con frecuencia.  
  
 **\/Oy** habilita la omisión del puntero de marco, mientras que **\/Oy\-** deshabilita la omisión. **\/Oy** solo está disponible en compiladores x86.  
  
 Si el código requiere direccionamiento basado en EBP, puede especificar la opción **\/Oy–** después de **\/Ox** o utilizar [optimize](../../preprocessor/optimize.md) con los argumentos "**y**" y **off** para obtener una optimización máxima con dicho direccionamiento.  El compilador detecta la mayoría de las situaciones en las que se requiere el direccionamiento basado en EBP \(por ejemplo, con las funciones `_alloca` y `setjmp` y con el control de excepciones estructurado\).  
  
 Las opciones [\/Ox \(Optimización completa\)](../../build/reference/ox-full-optimization.md) y [\/O1, \/O2 \(Minimizar tamaño, maximizar velocidad\)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) implican **\/Oy**.  Si se especifica **\/Oy–** después de la opción **\/Ox**, **\/O1** u **\/O2**, se deshabilita **\/Oy**, tanto si está explícito como si está implícito.  
  
 La opción **\/Oy** del compilador dificulta el uso del depurador, ya que el compilador suprime la información de los punteros de marco.  Si especifica una opción del compilador para depuración \([\/Z7, \/Zi, \/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)\), es recomendable especificar la opción **\/Oy\-** después de cualquier otra opción de optimización del compilador.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Optimización**.  
  
4.  Modifique la propiedad **Omitir punteros de marcos**.  Esta propiedad solo agrega o quita la opción **\/Oy**.  Si desea agregar la opción **\/Oy\-**, haga clic en **Línea de Comandos** y modifique **Opciones adicionales**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitFramePointers%2A>.  
  
## Vea también  
 [\/O \(Opciones\) \(Optimizar código\)](../../build/reference/o-options-optimize-code.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)