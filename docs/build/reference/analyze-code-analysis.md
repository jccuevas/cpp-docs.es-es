---
title: "/analyze (an&#225;lisis de c&#243;digo) | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.EnablePREfast"
  - "/analyze"
  - "VC.Project.VCCLCompilerTool.PREfastAdditionalOptions"
  - "VC.Project.VCCLCompilerTool.PREfastAdditionalPlugins"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/analyze (opción del compilador) [C++]"
  - "analyze (opción del compilador) [C++]"
  - "-analyze (opción del compilador) [C++]"
ms.assetid: 81da536a-e030-4bd4-be18-383927597d08
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /analyze (an&#225;lisis de c&#243;digo)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Permite utilizar análisis de código y opciones de control.  
  
## Sintaxis  
  
```  
/analyze[-][:WX-][:log filename][:quiet][:stacksize number][:max_paths number][:only]  
```  
  
## Argumentos  
 \/analyze  
 Activa el análisis en el modo predeterminado.  El resultado del análisis se pasa a la ventana **Resultados** como otros mensajes de error.  Use **\/analyze\-** para desactivar explícitamente el análisis.  
  
 \/analyze:WX\-  
 Si se especifica **\/analyze:WX\-**, las advertencias de análisis de código no se tratan como errores al realizar la compilación con **\/WX**.  Para obtener más información, vea [\/w, \/Wn, \/WX, \/Wall, \/wln, \/wdn, \/wen, \/won \(Nivel de advertencia\)](../../build/reference/compiler-option-warning-level.md).  
  
 \/analyze:log `filename`  
 Los resultados detallados del analizador se escriben como XML en el archivo especificado por `filename`.  
  
 \/analyze:quiet  
 Desactiva los resultados del analizador en la ventana **Resultados**.  
  
 \/analyze:stacksize `number`  
 El parámetro `number` que se utiliza con esta opción especifica el tamaño, en bytes, del marco de pila en el que se genera la advertencia [C6262](../Topic/C6262.md).  Si no se especifica este parámetro, el tamaño del marco de pila se establece de forma predeterminada en 16 KB.  
  
 \/analyze:max\_paths `number`  
 El parámetro `number` que se utiliza con esta opción especifica el número máximo de rutas de acceso del código que se van a analizar.  Si no se especifica este parámetro, el número se establece de forma predeterminada en 256.  Si se utilizan valores más elevados, se realizará una comprobación más completa, pero el análisis podría llevar más tiempo.  
  
 \/analyze:only  
 Normalmente, el compilador genera código y realiza una mayor comprobación de la sintaxis después de ejecutar el analizador.  La opción **\/analyze:only** desactiva este paso de generación de código. De este modo, el análisis se realiza más rápido, pero no se muestran las advertencias y errores de compilación que podrían detectarse en el paso de generación de código del compilador.  Si el programa no contiene errores de generación de código, es posible que los resultados del análisis no sean confiables; por tanto, es recomendable que solo use esta opción si el código ha pasado previamente comprobaciones de sintaxis de generación de código sin errores.  
  
## Comentarios  
 Para obtener más información, vea [Análisis de código para obtener información general de C\/C\+\+](../Topic/Code%20Analysis%20for%20C-C++%20Overview.md) y [Advertencias de análisis de código de C\/C\+\+](../Topic/Code%20Analysis%20for%20C-C++%20Warnings.md).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Expanda el nodo **Propiedades de configuración**.  
  
3.  Expanda el nodo **Análisis de código**.  
  
4.  Seleccione la página de propiedades **General**.  
  
5.  Modifique una o varias de las propiedades de **Análisis de código**.  
  
### Para establecer esta opción del compilador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)