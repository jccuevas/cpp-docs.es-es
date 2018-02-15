---
title: -w,-W0,-W1, - W2,-W3, - W4,-w1,-w2,-w3,-w4,-Wall, -wd,-se, -wo, -Wv, - WX (nivel de advertencia) | Documentos de Microsoft
ms.custom: 
ms.date: 01/31/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: be7e86065b52ee5c55058b9a672f3bf543454cf8
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="w-w0-w1-w2-w3-w4-w1-w2-w3-w4-wall-wd-we-wo-wv-wx-warning-level"></a>/ w, / W0, /W1, /W2, /W3, / W4, /w1, /w2, /w3, / W4, / Wall, /wd, / se, /wo, / wv, /WX (nivel de advertencia)

Especifica cómo el compilador genera advertencias para una compilación dada.

## <a name="syntax"></a>Sintaxis

> **/w**  
> **/W0**  
> **/W1**  
> **/W2**  
> **/W3**  
> **/W4**  
> **/Wall**  
> **/Wv**\[**:**_version_]  
> **/WX**  
> **/W1**_advertencia_  
> **/W2**_advertencia_  
> **/W3**_advertencia_  
> **/ W4**_advertencia_  
> **/wd**_warning_  
> **/we**_advertencia_  
> **/wo**_advertencia_  

## <a name="remarks"></a>Comentarios

Las opciones de advertencia especifican qué advertencias del compilador para mostrar y el comportamiento de advertencia para la compilación completo.

En la tabla siguiente se describen las opciones de advertencia y los argumentos relacionados:

|Opción|Descripción|
------------|-----------------|
|**/w**|Suprime todas las advertencias del compilador.|
|**/W0**<br /><br /> **/W1**<br /><br /> **/W2**<br /><br /> **/W3**<br /><br /> **/W4**|Especifica el nivel de advertencias que se ha generado por el compilador. Los niveles de advertencia válidos oscilan entre 0 y 4:<br />**/ W0** suprime todas las advertencias. Esto equivale a **/w**.<br />**/ W1** muestra advertencias de nivel 1 (severas). **/ W1** es la configuración predeterminada en el compilador de línea de comandos.<br />**/ W2** muestra nivel 1 y nivel 2 advertencias (importantes).<br />**/ W3** muestra nivel 1, nivel 2 y avisos de nivel 3 (calidad de producción). **/ W3** es la configuración predeterminada en el IDE.<br />**/ W4** muestra nivel 1, nivel 2 y avisos de nivel 3, y todo el nivel 4 advertencias (informativas) que no están desactivadas de forma predeterminada. Se recomienda que use esta opción para proporcionar advertencias similares a quitar. Para un proyecto nuevo, puede ser más conveniente usar **/W4** en todas las compilaciones; Esto garantizará el menor número de defectos de código difícil de encontrar posibles.|
|**/Wall**|Muestra todas las advertencias que se muestran por **/W4** y todas las demás advertencias que **/W4** no incluye, por ejemplo, las advertencias que están desactivadas de forma predeterminada. Para obtener más información, consulte [compilador advertencias que está desactivado de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).|
|**/Wv**\[**:**_version_]|Muestra solo las advertencias introducidas en la versión del compilador *versión* y versiones anteriores. Puede usar esta opción para suprimir las advertencias nuevo en el código cuando se migra a una versión más reciente del compilador y para mantener el proceso de compilación existente mientras se corregirlos. El parámetro opcional *versión* toma la forma  *nn* [. *mm*[. *bbbbb*]] donde  *nn*  es el número de versión principal, *mm* es el número de versión secundaria opcional y *bbbbb* es el número de compilación opcional del compilador. Por ejemplo, utilice */Wv:17* para mostrar las advertencias introducidas en Visual Studio 2012 (es decir, cualquier versión del compilador que tiene un número de versión principal de 17) o una versión anterior, pero suprimir las advertencias introducidas en Visual Studio 2013 (versión principal 18) y versiones posteriores. De forma predeterminada, **/wv** utiliza el número de versión del compilador actual y sin advertencias se suprimen. Para obtener información sobre los cuales se suprimen las advertencias por versión del compilador, vea [advertencias del compilador por versión del compilador](../..//error-messages/compiler-warnings/compiler-warnings-by-compiler-version.md).|
|**/WX**|Trata todas las advertencias del compilador como errores. Para un proyecto nuevo, puede ser más conveniente usar **/WX** en todas las compilaciones; resolver todas las advertencias asegura el menor número de defectos de código difícil de encontrar posibles.<br /><br /> El vinculador también tiene una **/WX** opción. Para obtener más información, consulte [/WX (Tratar advertencias del enlazador como errores)](../../build/reference/wx-treat-linker-warnings-as-errors.md).|
|**/w1**_nnnn_<br /><br /> **/w2**_nnnn_<br /><br /> **/w3**_nnnn_<br /><br /> **/w4**_nnnn_|Establece el nivel de advertencia para el número de advertencia especificado por  _nnnn_ . Esto le permite cambiar el comportamiento del compilador para dicha advertencia cuando se establece un nivel de advertencia específico. Puede usar estas opciones en combinación con otras opciones de advertencia para aplicar los estándares de sus propio código para las advertencias, en lugar de los predeterminados suministrados por Visual Studio.<br /><br /> Por ejemplo, **/w34326** hace que C4326 se genere como una advertencia de nivel 3 en lugar de nivel 1. Si se compila con ambos el **/w34326** opción y la **/W2** opción, advertencia C4326 no se genera.|
|**/wd**_nnnn_|Suprime la advertencia del compilador especificado por  _nnnn_ .<br /><br /> Por ejemplo, **/wd4326** suprime la advertencia de compilador C4326.|
|**/we**_nnnn_|Trata la advertencia del compilador especificado por  _nnnn_  como un error.<br /><br /> Por ejemplo, **/we4326** hace que el número de advertencia C4326 se trate como un error por el compilador.|
|**/wo**_nnnn_|El compilador de advertencia que es especificada por los informes  _nnnn_  una sola vez.<br /><br /> Por ejemplo, **/wo4326** causas advertencia C4326 se comunique una sola vez, la primera vez que se encuentra por el compilador.|

Si usa cualquiera de las opciones de advertencia cuando se crea un encabezado precompilado utilizando la [/Yc](../../build/reference/yc-create-precompiled-header-file.md) opción, cualquier uso del encabezado precompilado utilizando la [/Yu](../../build/reference/yu-use-precompiled-header-file.md) opción hace que las mismas opciones de advertencia a estar en vigor volver a ejecutarlo. Puede invalidar las opciones de advertencia establecidas en el encabezado precompilado con otra opción de advertencia en la línea de comandos.

Puede usar un [#pragma warning](../../preprocessor/warning.md) directiva para controlar el nivel de advertencia que se notifica en tiempo de compilación en archivos de origen específico.

Directivas pragma de advertencia en el código fuente no se ven afectadas por la **/w** opción.

El [documentación sobre errores de compilación](../../error-messages/compiler-errors-1/c-cpp-build-errors.md) describe las advertencias y los niveles de advertencia e indica por qué ciertas instrucciones no pueden compilarse según lo esperado.

### <a name="to-set-the-compiler-options-in-the-visual-studio-development-environment"></a>Para establecer las opciones del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Para establecer el **/W0**, **/W1**, **/W2**, **/W3**, **/W4**, **/pared**m **/Wv**, **/WX** o **/WX-** opciones, seleccionadas la **propiedades de configuración** > **C / C++** > **General** página de propiedades.

   - Para establecer el **/W0**, **/W1**, **/W2**, **/W3**, **/W4**, o **/pared** Opciones, modifique la **nivel de advertencia** propiedad.

   - Para establecer el **/WX** o **/WX-** opciones, modifique la **tratar advertencias como errores** propiedad.

   - Para establecer la versión de la **/wv** opción, especifique el número de versión del compilador en el **advertencia versión** propiedad.

1. Para establecer el **/wd** o **/we** opciones, seleccionadas la **propiedades de configuración** > **C/C++**  >   **Advanced** página de propiedades.

   - Para establecer el **/wd** opción, seleccione la **deshabilitar advertencias específicas** propiedad lista desplegable del control y, a continuación, elija **editar**. En el cuadro de edición en el **deshabilitar advertencias específicas** cuadro de diálogo, escriba el número de advertencia. Para especificar más de una advertencia, separe los valores con un punto y coma (**;**). Por ejemplo, para deshabilitar C4001 y C4010, escriba **4001; 4010**. Elija **Aceptar** para guardar los cambios y volver a la **páginas de propiedades** cuadro de diálogo.

   - Para establecer el **/we** opción, seleccione la **tratar advertencias como errores específicos** propiedad lista desplegable del control y, a continuación, elija **editar**. En el cuadro de edición en el **tratar advertencias como errores específicos** cuadro de diálogo, escriba el número de advertencia. Para especificar más de una advertencia, separe los valores con un punto y coma (**;**). Por ejemplo, para tratar C4001 y C4010 como errores, escriba **4001; 4010**. Elija **Aceptar** para guardar los cambios y volver a la **páginas de propiedades** cuadro de diálogo.

1. Para establecer el **/wo** opción, seleccione la **propiedades de configuración** > **C/C++** > **línea de comandos** página de propiedades. Escriba la opción del compilador en el **opciones adicionales** cuadro.

1. Elija **Aceptar** para guardar los cambios.

### <a name="to-set-the-compiler-option-programmatically"></a>Para establecer la opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarnAsError%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableSpecificWarnings%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)  
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)  
