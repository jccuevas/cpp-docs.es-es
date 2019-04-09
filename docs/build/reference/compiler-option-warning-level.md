---
title: / w, / W0, / W1, / W2, / w3, / W4, / W1, / W2, / w3, / W4, / Wall, / WD, / we, / WO, / wv, /WX (nivel de advertencia)
ms.date: 01/31/2018
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
ms.openlocfilehash: 7b5c19c95cff3058bb3dcc6640f8ab07cf01edd6
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59040076"
---
# <a name="w-w0-w1-w2-w3-w4-w1-w2-w3-w4-wall-wd-we-wo-wv-wx-warning-level"></a>/ w, / W0, / W1, / W2, / w3, / W4, / W1, / W2, / w3, / W4, / Wall, / WD, / we, / WO, / wv, /WX (nivel de advertencia)

Especifica cómo el compilador genera advertencias para una compilación determinada.

## <a name="syntax"></a>Sintaxis

> **/w**
>  **/W0**
>  **/W1**
>  **/W2**
>  **/w3** 
>  **/W4**
>  **/Wall**
>  **/wv**\[**:**_versión _] **/WX**
>  **/W1**_advertencia_
>  **/W2** _ advertencia_
>  **/w3**_advertencia_
>  **/W4**_advertencia_ 
>  **/wd**_advertencia_
>  **/we**_advertencia_ 
>  **/wo**_advertencia_

## <a name="remarks"></a>Comentarios

Las opciones de advertencia especifican qué advertencias del compilador para mostrar y el comportamiento de advertencia para la compilación completa.

En la tabla siguiente se describen las opciones de advertencia y los argumentos relacionados:

|Opción|Descripción|
------------|-----------------|
|**/w**|Suprime todas las advertencias del compilador.|
|**/W0**<br /><br /> **/W1**<br /><br /> **/W2**<br /><br /> **/W3**<br /><br /> **/W4**|Especifica el nivel de advertencias que se genera el compilador. Los niveles válidos van de 0 a 4:<br />**/ W0** suprime todas las advertencias. Esto es equivalente a **/w**.<br />**/ W1** muestra advertencias de nivel 1 (gravedad). **/ W1** es la configuración predeterminada en el compilador de línea de comandos.<br />**/ W2** muestra el nivel 1 y advertencias de nivel 2 (importantes).<br />**/ W3** muestra el nivel 1, nivel 2 y avisos de nivel 3 (calidad de producción). **/ W3** es la configuración predeterminada en el IDE.<br />**/ W4** muestra de nivel 1, nivel 2 y avisos de nivel 3 y 4 advertencias (informativas) que no están desactivadas de forma predeterminada el nivel todos. Se recomienda que use esta opción para proporcionar advertencias similar a lint. Para un nuevo proyecto, puede ser mejor usar **/W4** en todas las compilaciones; Esto garantizará el menor número de defectos de código difícil de encontrar posibles.|
|**/Wall**|Muestra todas las advertencias que se muestran por **/W4** y todas las demás advertencias que **/W4** no incluye, por ejemplo, las advertencias que están desactivadas de forma predeterminada. Para obtener más información, consulte [compilador advertencias que está desactivado de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).|
|**/ Wv**\[**:**_versión_]|Muestra solo advertencias introducidas en la versión del compilador *versión* y versiones anteriores. Puede usar esta opción para suprimir las advertencias nuevas en el código al migrar a una versión más reciente del compilador y para mantener el proceso de compilación existente mientras se corregirlos. El parámetro opcional *versión* adopta la forma *nn*[. *mm*[. *bbbbb*]] donde *nn* es el número de versión principal, *mm* es el número de versión secundaria opcional y *bbbbb* es el número de compilación opcional el compilador. Por ejemplo, usar */Wv:17* para mostrar advertencias introducidas en Visual Studio 2012 (es decir, cualquier versión del compilador que tiene un número de versión principal de 17) o una versión anterior, pero suprimir las advertencias introducidas en Visual Studio 2013 (versión principal 18) y versiones posteriores. De forma predeterminada, **/wv** usa el número de versión del compilador actual y sin advertencias se han suprimido. Para obtener información sobre qué advertencias se han suprimido por versión del compilador, vea [advertencias del compilador por versión del compilador](../../error-messages/compiler-warnings/compiler-warnings-by-compiler-version.md).|
|**/WX**|Trata todas las advertencias del compilador como errores. Para un nuevo proyecto, puede ser mejor usar **/WX** en todas las compilaciones; resolver todas las advertencias asegura el menor número de defectos de código difícil de encontrar posibles.<br /><br /> El vinculador también tiene un **/WX** opción. Para obtener más información, consulte [/WX (Tratar advertencias del enlazador como errores)](wx-treat-linker-warnings-as-errors.md).|
|**/w1**_nnnn_<br /><br /> **/w2**_nnnn_<br /><br /> **/w3**_nnnn_<br /><br /> **/w4**_nnnn_|Establece el nivel de advertencia para el número de advertencia especificado por _nnnn_. Esto le permite cambiar el comportamiento del compilador para que aparezca esa advertencia cuando se establece un nivel de advertencia específico. Puede usar estas opciones en combinación con otras opciones de advertencia para aplicar los estándares de sus propio código para advertencias en lugar de los valores predeterminados que proporciona Visual Studio.<br /><br /> Por ejemplo, **/w34326** que C4326 se genere como una advertencia de nivel 3 en lugar de nivel 1. Si compila con ambos métodos el **/w34326** opción y la **/W2** opción, no se genera C4326 de advertencia.|
|**/wd**_nnnn_|Suprime la advertencia del compilador especificado por _nnnn_.<br /><br /> Por ejemplo, **/wd4326** suprime la advertencia de compilador C4326.|
|**/we**_nnnn_|Trata la advertencia del compilador especificado por _nnnn_ como un error.<br /><br /> Por ejemplo, **/we4326** hace que el número de advertencia C4326 se trate como un error por el compilador.|
|**/wo**_nnnn_|Informes de la advertencia del compilador que es especificada por _nnnn_ una sola vez.<br /><br /> Por ejemplo, **/wo4326** causas advertencia C4326 se comunique con una sola vez, la primera vez se encuentra el compilador.|

Si usa cualquiera de las opciones de advertencia cuando se crea un encabezado precompilado utilizando la [/Yc](yc-create-precompiled-header-file.md) opción, cualquier uso del encabezado precompilado utilizando la [/Yu](yu-use-precompiled-header-file.md) opción hace que las mismas opciones de advertencia a estar en vigor de nuevo. Puede invalidar las opciones de advertencia establecidas en el encabezado precompilado con otra opción de advertencia en la línea de comandos.

Puede usar un [advertencia #pragma](../../preprocessor/warning.md) directiva para controlar el nivel de advertencia que es notificado en tiempo de compilación en los archivos de origen específico.

Directivas de advertencia pragma en el código fuente se ven afectadas por la **/w** opción.

El [documentación sobre errores de compilación](../../error-messages/compiler-errors-1/c-cpp-build-errors.md) describe las advertencias y los niveles de advertencia y se indica por qué algunas instrucciones no pueden compilarse según lo esperado.

### <a name="to-set-the-compiler-options-in-the-visual-studio-development-environment"></a>Para establecer las opciones del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Para establecer el **/W0**, **/W1**, **/W2**, **/w3**, **/W4**, **/Wall**, **/Wv**, **/WX** o **/WX-** opciones, seleccionadas el **propiedades de configuración** > **C / C++** > **General** página de propiedades.

   - Para establecer el **/W0**, **/W1**, **/W2**, **/w3**, **/W4**, o **/Wall** modificar opciones, el **nivel de advertencia** propiedad.

   - Para establecer el **/WX** o **/WX-** modificar opciones, el **tratar advertencias como errores** propiedad.

   - Para establecer la versión de la **/wv** opción, especifique el número de versión del compilador en el **versión de la advertencia** propiedad.

1. Para establecer el **/wd** o **/we** opciones, seleccionadas el **propiedades de configuración** > **C o C++**  >   **Advanced** página de propiedades.

   - Para establecer el **/wd** opción, seleccione el **deshabilitar advertencias específicas** propiedad control lista desplegable y, a continuación, elija **editar**. En el cuadro de edición en el **deshabilitar advertencias específicas** cuadro de diálogo, escriba el número de advertencia. Para especificar más de una advertencia, sepárelos por punto y coma (**;**). Por ejemplo, para deshabilitar C4001 y C4010, escriba **4001; 4010**. Elija **Aceptar** para guardar los cambios y volver a la **páginas de propiedades** cuadro de diálogo.

   - Para establecer el **/we** opción, seleccione el **tratar advertencias específicas como errores** propiedad control lista desplegable y, a continuación, elija **editar**. En el cuadro de edición en el **tratar advertencias específicas como errores** cuadro de diálogo, escriba el número de advertencia. Para especificar más de una advertencia, sepárelos por punto y coma (**;**). Por ejemplo, para tratar C4001 y C4010 como errores, escriba **4001; 4010**. Elija **Aceptar** para guardar los cambios y volver a la **páginas de propiedades** cuadro de diálogo.

1. Para establecer el **/wo** opción, seleccione el **propiedades de configuración** > **C o C++** > **línea de comandos** página de propiedades. Especifique la opción del compilador en el **opciones adicionales** cuadro.

1. Elija **Aceptar** para guardar los cambios.

### <a name="to-set-the-compiler-option-programmatically"></a>Para establecer la opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarnAsError%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableSpecificWarnings%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
