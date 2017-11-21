---
title: -w,-W0,-W1, - W2,-W3, - W4,-w1,-w2,-w3,-w4,-Wall, -wd,-se, -wo, -Wv, - WX (nivel de advertencia) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.DisableSpecificWarnings
- VC.Project.VCCLCompilerTool.WarningLevel
- VC.Project.VCCLWCECompilerTool.DisableSpecificWarnings
- VC.Project.VCCLCompilerTool.WarnAsError
- VC.Project.VCCLWCECompilerTool.WarnAsError
- /wx
- VC.Project.VCCLWCECompilerTool.WarningLevel
- /wall
- VC.Project.VCCLCompilerTool.TreatSpecificWarningsAsErrors
- /Wv
- /w0
- /w1
- /w2
- /w3
- /w4
- /wd
- /we
- /wo
dev_langs: C++
helpviewer_keywords:
- /W1 compiler option [C++]
- w compiler option [C++]
- -wo compiler option [C++]
- Warning Level compiler option
- W1 compiler option [C++]
- -we compiler option [C++]
- /WX compiler option [C++]
- -wd compiler option [C++]
- WX compiler option [C++]
- wo compiler option [C++]
- Wall compiler option [C++]
- /w compiler option
- W2 compiler option [C++]
- -W2 compiler option [C++]
- wd compiler option [C++]
- /we compiler option [C++]
- we compiler option [C++]
- -W1 compiler option [C++]
- -W4 compiler option [C++]
- -Wall compiler option [C++]
- /Wall compiler option [C++]
- -W0 compiler option [C++]
- W0 compiler option [C++]
- -WX compiler option [C++]
- /wo compiler option [C++]
- W4 compiler option [C++]
- W3 compiler option [C++]
- /wd compiler option [C++]
- warnings, as errors compiler option
- /W3 compiler option [C++]
- /W0 compiler option [C++]
- /W4 compiler option [C++]
- -W3 compiler option [C++]
- -w compiler option [C++]
- /W2 compiler option [C++]
- /Wv compiler option [C++]
ms.assetid: d6bc7bf5-c754-4879-909c-8e3a67e2629f
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5504c3d726feda499fb4b63f68d7784291308694
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="w-w0-w1-w2-w3-w4-w1-w2-w3-w4-wall-wd-we-wo-wv-wx-warning-level"></a>/ w, / W0, /W1, /W2, /W3, / W4, /w1, /w2, /w3, / W4, / Wall, /wd, / se, /wo, / wv, /WX (nivel de advertencia)
Especifica cómo el compilador genera advertencias para una compilación dada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/w  
/W0  
/W1  
/W2  
/W3  
/W4  
/Wall  
/Wv[<version>]  
/WX  
/w1<warning>   
/w2<warning>   
/w3<warning>   
/w4<warning>   
/wd<warning>   
/we<warning>   
/wo<warning>  
```  
  
## <a name="remarks"></a>Comentarios  
 Las opciones de advertencia especifican qué advertencias del compilador para mostrar y el comportamiento de advertencia para la compilación completo.  
  
 En la tabla siguiente se describen las opciones de advertencia y los argumentos relacionados:  
  
|Opción|Descripción|  
|------------|-----------------|  
|**/ w**|Suprime todas las advertencias del compilador.|  
|**/W0**<br /><br /> **/W1**<br /><br /> **/W2**<br /><br /> **/W3**<br /><br /> **/W4**|Especifica el nivel de advertencias que se ha generado por el compilador. Los niveles de advertencia válidos oscilan entre 0 y 4:<br /><br /> -   **/ W0** suprime todas las advertencias.<br />-   **/ W1** muestra advertencias de nivel 1 (severas). **/ W1** es la configuración predeterminada.<br />-   **/ W2** muestra nivel 1 y nivel 2 advertencias (importantes).<br />-   **/ W3** muestra nivel 1, nivel 2 y avisos de nivel 3 (calidad de producción).<br />-   **/ W4** muestra nivel 1, nivel 2 y avisos de nivel 3, y todo el nivel 4 advertencias (informativas) que no están desactivadas de forma predeterminada. Se recomienda que use esta opción solo para proporcionar advertencias similares a quitar. Sin embargo, para un proyecto nuevo, puede ser mejor usar **/W4** en todas las compilaciones; Esto garantizará el menor número de defectos de código difícil de encontrar posibles.|  
|**/ Wall**|Muestra todas las advertencias que se muestran por **/W4** y todas las demás advertencias que **/W4** no incluye, por ejemplo, las advertencias que están desactivadas de forma predeterminada. Para obtener más información, consulte [compilador advertencias que está desactivado de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).|  
|**/ Wv**`:version`|Suprimir las advertencias introducidas en las versiones del compilador más recientes que `version`. Puede usar esta opción para determinar si hay nuevas advertencias en el código compilado sin advertencias cuando se usa una versión anterior del compilador y para suprimir temporalmente las advertencias nuevo desde el proceso de compilación, mientras que corregirlos. El parámetro opcional `version` toma la forma `nn`[.`mm` [. `bbbbb`]] donde `nn` es el número de versión principal, `mm` es el número de versión secundaria opcional, y `bbbbb` es el número de versión opcional del compilador. Por ejemplo, utilice `/Wv:17.00.00000` para suprimir las advertencias introducidas en Visual C++ 2012 y versiones posteriores. De forma predeterminada, **/wv** utiliza el número de versión del compilador actual y sin advertencias se suprimen. Para obtener información sobre los cuales se suprimen las advertencias por versión del compilador, vea [advertencias del compilador por versión del compilador](../..//error-messages/compiler-warnings/compiler-warnings-by-compiler-version.md).|  
|**/WX**|Trata todas las advertencias del compilador como errores. Para un proyecto nuevo, puede ser más conveniente usar **/WX** en todas las compilaciones; resolver todas las advertencias asegura el menor número de defectos de código difícil de encontrar posibles.<br /><br /> El vinculador también tiene una **/WX** opción. Para obtener más información, consulte [/WX (Tratar advertencias del enlazador como errores)](../../build/reference/wx-treat-linker-warnings-as-errors.md).|  
|**/W1**`n`<br /><br /> **/W2**`n`<br /><br /> **/W3**`n`<br /><br /> **/ W4**`n`|Establece el nivel de advertencia para el número de advertencia especificado por `n`. Esto le permite cambiar el comportamiento del compilador para dicha advertencia cuando se establece un nivel de advertencia específico. Puede usar estas opciones en combinación con otras opciones de advertencia para aplicar los estándares de sus propio código para las advertencias, en lugar de los predeterminados suministrados por Visual Studio.<br /><br /> Por ejemplo, `/w34326` hace que C4326 se genere como una advertencia de nivel 3 en lugar de nivel 1. Si se compila con ambos el `/w34326` opción y `/W2` opción, advertencia C4326 no se genera.|  
|**/wd**`n`|Suprime la advertencia del compilador especificado por `n`.<br /><br /> Por ejemplo, `/wd4326` suprime la advertencia de compilador C4326.|  
|**/we**`n`|Trata la advertencia del compilador especificado por `n` como un error.<br /><br /> Por ejemplo, `/we4326` hace que el número de advertencia C4326 se trate como un error por el compilador.|  
|**/wo**`n`|El compilador de advertencia que es especificada por los informes `n` una sola vez.<br /><br /> Por ejemplo, `/wo4326` causas advertencia C4326 se comunique una sola vez, la primera vez que se encuentra por el compilador.|  
  
 Si usa cualquiera de las opciones de advertencia cuando se crea un encabezado precompilado utilizando la [/Yc](../../build/reference/yc-create-precompiled-header-file.md) opción, cualquier uso del encabezado precompilado utilizando la [/Yu](../../build/reference/yu-use-precompiled-header-file.md) opción hace que las mismas opciones de advertencia a estar en vigor volver a ejecutarlo. Puede invalidar las opciones de advertencia establecidas en el encabezado precompilado con otra opción de advertencia en la línea de comandos.  
  
 Puede usar un [#pragma warning](../../preprocessor/warning.md) directiva para controlar el nivel de advertencia que se notifica en tiempo de compilación en archivos de origen específico.  
  
 Directivas de advertencia pragma en el código fuente no se ven afectadas por la **/w** opción.  
  
 El [documentación sobre errores de compilación](../../error-messages/compiler-errors-1/c-cpp-build-errors.md) describe las advertencias y los niveles de advertencia e indica por qué ciertas instrucciones no pueden compilarse según lo esperado.  
  
### <a name="to-set-the-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer la opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione **C/C++**.  
  
3.  En el **General** propiedad, modifique la **nivel de advertencia** o **tratar advertencias como errores** propiedades.  
  
4.  En el **avanzadas** propiedad, modifique la **deshabilitar advertencias específicas** propiedad.  
  
5.  Para el resto de opciones, en el **línea de comandos** propiedad página, escriba la opción del compilador en el **opciones adicionales** cuadro.  
  
### <a name="to-set-the-compiler-option-programmatically"></a>Para establecer la opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarnAsError%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableSpecificWarnings%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)