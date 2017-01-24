---
title: "/w, /Wn, /WX, /Wall, /wln, /wdn, /wen, /won (Nivel de advertencia) | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.DisableSpecificWarnings"
  - "VC.Project.VCCLCompilerTool.WarningLevel"
  - "VC.Project.VCCLWCECompilerTool.DisableSpecificWarnings"
  - "VC.Project.VCCLCompilerTool.WarnAsError"
  - "VC.Project.VCCLWCECompilerTool.WarnAsError"
  - "/wx"
  - "VC.Project.VCCLWCECompilerTool.WarningLevel"
  - "/wall"
  - "VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors"
  - "/Wv"
  - "/w0"
  - "/w1"
  - "/w2"
  - "/w3"
  - "/w4"
  - "/wd"
  - "/we"
  - "/wo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/w (opción del compilador)"
  - "/W0 (opción del compilador) [C++]"
  - "/W1 (opción del compilador) [C++]"
  - "/W2 (opción del compilador) [C++]"
  - "/W3 (opción del compilador) [C++]"
  - "/W4 (opción del compilador) [C++]"
  - "/Wall (opción del compilador) [C++]"
  - "/wd (opción del compilador) [C++]"
  - "/we (opción del compilador) [C++]"
  - "/wo (opción del compilador) [C++]"
  - "/WX (opción del compilador) [C++]"
  - "w (opción del compilador) [C++]"
  - "-w (opción del compilador) [C++]"
  - "W0 (opción del compilador) [C++]"
  - "-W0 (opción del compilador) [C++]"
  - "W1 (opción del compilador) [C++]"
  - "-W1 (opción del compilador) [C++]"
  - "W2 (opción del compilador) [C++]"
  - "-W2 (opción del compilador) [C++]"
  - "W3 (opción del compilador) [C++]"
  - "-W3 (opción del compilador) [C++]"
  - "W4 (opción del compilador) [C++]"
  - "-W4 (opción del compilador) [C++]"
  - "Wall (opción del compilador) [C++]"
  - "-Wall (opción del compilador) [C++]"
  - "Nivel de advertencia (opción del compilador)"
  - "advertencias, como errores (opción del compilador)"
  - "wd (opción del compilador) [C++]"
  - "-wd (opción del compilador) [C++]"
  - "we (opción del compilador) [C++]"
  - "-we (opción del compilador) [C++]"
  - "wo (opción del compilador) [C++]"
  - "-wo (opción del compilador) [C++]"
  - "WX (opción del compilador) [C++]"
  - "-WX (opción del compilador) [C++]"
ms.assetid: d6bc7bf5-c754-4879-909c-8e3a67e2629f
caps.latest.revision: 21
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /w, /Wn, /WX, /Wall, /wln, /wdn, /wen, /won (Nivel de advertencia)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica cómo el compilador genera las advertencias para una compilación determinada.  
  
## Sintaxis  
  
```  
/w  
/Wn  
/WX  
/Wall  
/wln  
/wdn  
/wen  
/won  
```  
  
## Comentarios  
 Las opciones y los argumentos relacionados se describen en la tabla siguiente.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**\/w**|Deshabilita todas las advertencias del compilador.|  
|**\/W** `n`|Especifica el nivel de advertencia de ser generado por el compilador.  Los niveles válidos para `n` pueden tomar valores entre 0 y 4:<br /><br /> -   En el nivel 0 se deshabilitan todas las advertencias.<br />-   En el nivel 1 se muestran las advertencias severas.  El nivel 1 es la configuración predeterminada.<br />-   El nivel 2 muestra todas las advertencias de nivel 1 y las advertencias que tengan menos graves que el nivel 1.<br />-   El nivel 3 muestra todas las advertencias de nivel 2 y el resto de las advertencias que se recomienda para la producción.<br />-   El nivel 4 muestra todas las advertencias de nivel 3 y advertencias informativas.  Se recomienda usar esta opción para proporcionar sólo pelusa\- como advertencias.  Sin embargo, para un nuevo proyecto, puede ser preferible utilizar `/W4` en todas las compilaciones; esto asegurará el menor de los defectos de código posibles de la duro\-a\- búsqueda.|  
|**\/Wall**|Muestra todas las advertencias de \/W4 y cualquier otra advertencia que no están incluidos en \/W4 \(por ejemplo, las advertencias que están desactivadas de forma predeterminada.  Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).|  
|**\/WX**|Trata todas las advertencias del compilador como errores.  Para un proyecto nuevo, puede ser más conveniente usar **\/WX** en todas las compilaciones; la resolución de todas las advertencias asegura el menor número posible de defectos de código de difícil localización.<br /><br /> El vinculador también tiene una opción de **\/WX** .  Para obtener más información, vea [\/WX \(Tratar advertencias del vinculador como errores\)](../../build/reference/wx-treat-linker-warnings-as-errors.md).|  
|**\/w** `ln`|Especifica el nivel de una advertencia concreta.  El primer parámetro establece el nivel de la advertencia \(lo mismo que **\/W**`n`\) y el segundo es el número de la advertencia.<br /><br /> Por ejemplo, `/w14326` hace que C4326 se genere como una advertencia de nivel 1.|  
|**\/wd** `n`|Deshabilita la advertencia del compilador que se especifica en `n`.<br /><br /> Por ejemplo, `/wd4326` deshabilita la advertencia de compilador C4326.|  
|**\/we** `n`|Trata como error la advertencia del compilador que se especifica en `n`.<br /><br /> Por ejemplo, `/we4326` marca el número de advertencia C4326 como un error.|  
|**\/wo** `n`|Notifica el error solo una vez para la advertencia del compilador que se especifica en `n`.<br /><br /> Por ejemplo, `/wo4326` genera la advertencia C4326 que se señalice sólo una vez.|  
  
 Si crea un encabezado precompilado \([\/Yc \(Crear archivo de encabezado precompilado\)](../../build/reference/yc-create-precompiled-header-file.md)\) utilizando una de las opciones de **\/w** , cualquier uso del encabezado precompilado \([\/Yu \(Utilizar el archivo de encabezado precompilado\)](../../build/reference/yu-use-precompiled-header-file.md)\) hace que los las opciones de **\/w** de ser en efecto de nuevo.  Puede reemplazar **\/w** que establece en el encabezado precompilado con otra opción de **\/w** en la línea de comandos.  
  
 Las directivas pragma en el código fuente no resultan afectadas por la opción **\/w**.  
  
 También puede utilizar [warning](../../preprocessor/warning.md) para controlar el nivel de advertencia que se notifica en tiempo de compilación.  
  
 [documentación de errores de compilación](../../error-messages/compiler-errors-1/c-cpp-build-errors.md) describe las advertencias y niveles de advertencia, e indica por qué algunas instrucciones pueden no compilarse como el esperado.  
  
### Para establecer la opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  **C\/C\+\+**Seleccione.  
  
3.  En la página de propiedades de **General** , modifique las propiedades de **Nivel de advertencia** o de **Tratar advertencias como errores** .  
  
4.  En la página de propiedades de **opciones avanzadas** , modifique la propiedad de **Deshabilitar advertencias específicas** .  
  
5.  Para las opciones restantes, en la página de propiedades de **Línea de comandos** , escriba la opción del compilador en el cuadro de **Opciones adicionales** .  
  
### Para establecer la opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarnAsError%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableSpecificWarnings%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)