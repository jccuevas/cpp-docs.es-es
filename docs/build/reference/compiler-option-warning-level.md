---
title: /w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (nivel de advertencia)
description: Referencia de las opciones de MicrosoftC++ C/Compiler:/W,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/We,/wo,/WV y/WX.
ms.date: 01/31/2020
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
ms.openlocfilehash: 80b6d0c1fe684de9af62683a75f0fd1107a94089
ms.sourcegitcommit: ba4180a2d79d7e391f2f705797505d4aedbc2a5e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2020
ms.locfileid: "76972170"
---
# <a name="w-w0-w1-w2-w3-w4-w1-w2-w3-w4-wall-wd-we-wo-wv-wx-warning-level"></a>/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (nivel de advertencia)

Especifica cómo el compilador genera advertencias para una compilación determinada.

## <a name="syntax"></a>Sintaxis

> **/w**\
> \ **/W0**
> \ **/W1**
> \ **/W2**
> \ **/W3**
> \ **/W4**
> **/Wall**\
> **/WV**\[ **:** _versión_] \
> **/Wx**\
> _ADVERTENCIA_ /W1\
> _ADVERTENCIA_ /W2\
> _ADVERTENCIA_ /W3\
> _ADVERTENCIA_ /W4\
> _advertencia_ de/WD\
> _ADVERTENCIA_ /We\
> _ADVERTENCIA_ de/WO

## <a name="remarks"></a>Notas

Las opciones de advertencia especifican qué advertencias del compilador deben mostrarse y el comportamiento de advertencia para toda la compilación.

Las opciones de advertencia y los argumentos relacionados se describen en las tablas siguientes:

Opción | Descripción
------ | -----------
**/w** | Suprime todas las advertencias del compilador.
**/W0**<br /><br /> **/W1**<br /><br /> **/W2**<br /><br /> **/W3**<br /><br /> **/W4** | Especifica el nivel de advertencias que va a generar el compilador. Los niveles de advertencia válidos van de 0 a 4:<br />**/W0** suprime todas las advertencias. Es equivalente a **/w**.<br />**/W1** muestra las advertencias de nivel 1 (grave). **/W1** es el valor predeterminado en el compilador de línea de comandos.<br />**/W2** muestra advertencias de nivel 1 y nivel 2 (importantes).<br />**/W3** muestra las advertencias de nivel 1, nivel 2 y nivel 3 (calidad de producción). **/W3** es el valor predeterminado en el IDE.<br />**/W4** muestra las advertencias de nivel 1, nivel 2 y nivel 3, y todas las advertencias de nivel 4 (informativo) que no están desactivadas de forma predeterminada. Se recomienda usar esta opción para proporcionar advertencias similares a las de pelusa. Para un proyecto nuevo, puede ser mejor utilizar **/W4** en todas las compilaciones. Esta opción ayuda a garantizar el menor número posible de defectos de código difíciles de encontrar.
**/Wall** | Muestra todas las advertencias que muestra **/W4** y todas las demás advertencias que **/W4** no incluye (por ejemplo, las advertencias que están desactivadas de forma predeterminada). Para obtener más información, vea [advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).
**/WV**\[ **:** _versión_] | Muestra solo las advertencias introducidas en la versión del compilador de *versión* y versiones anteriores. Puede usar esta opción para suprimir nuevas advertencias en el código al migrar a una versión más reciente del compilador. Permite mantener el proceso de compilación existente mientras se corrige. La *versión* del parámetro opcional adopta la forma *nn*\[. *mm*\[. *BBBBB*]], donde *nn* es el número de versión principal, *mm* es el número de versión secundaria opcional y *BBBBB* es el número de compilación opcional del compilador. Por ejemplo, use **/WV: 17** para mostrar solo las advertencias introducidas en Visual Studio 2012 (versión principal 17) o versiones anteriores. Es decir, muestra las advertencias de cualquier versión del compilador que tenga un número de versión principal de 17 o menos. Suprime las advertencias introducidas en Visual Studio 2013 (versión 18) y versiones posteriores. De forma predeterminada, **/WV** usa el número de versión del compilador actual y no se suprime ninguna advertencia. Para obtener información sobre qué advertencias se suprimen por versión del compilador, vea [advertencias del compilador por versión del compilador](../../error-messages/compiler-warnings/compiler-warnings-by-compiler-version.md).
**/WX** | Trata todas las advertencias del compilador como errores. Para un proyecto nuevo, puede ser mejor usar **/WX** en todas las compilaciones. la resolución de todas las advertencias garantiza el menor número posible de defectos de código difíciles de encontrar.<br /><br /> El enlazador también tiene una opción **/WX** . Para obtener más información, vea [/WX (Tratar advertencias del enlazador como errores)](wx-treat-linker-warnings-as-errors.md).

Las siguientes opciones se excluyen mutuamente entre sí. La última opción que se especifica de este grupo es la que se aplica:

Opción | Descripción
------ | -----------
**/w1**_nnnn_<br /><br /> **/w2**_nnnn_<br /><br /> **/w3**_nnnn_<br /><br /> **/w4**_nnnn_ | Establece el nivel de advertencia para el número de advertencia especificado por _nnnn_. Estas opciones permiten cambiar el comportamiento del compilador de esa advertencia cuando se establece un nivel de advertencia específico. Puede usar estas opciones en combinación con otras opciones de advertencia para aplicar sus propias normas de codificación para advertencias, en lugar de las predeterminadas proporcionadas por Visual Studio.<br /><br /> Por ejemplo, **/w34326** hace que C4326 se genere como una advertencia de nivel 3 en lugar de nivel 1. Si compila con la opción **/w34326** y la opción **/W2** , la advertencia C4326 no se genera.
**/wd**_nnnn_ | Suprime la advertencia del compilador especificada por _nnnn_.<br /><br /> Por ejemplo, **/wd4326** suprime la advertencia del compilador C4326.
**/we**_nnnn_ | Trata la advertencia del compilador especificada por _nnnn_ como un error.<br /><br /> Por ejemplo, **/we4326** provoca que el compilador trate el número de advertencia C4326 como un error.
**/wo**_nnnn_ | Notifica la advertencia del compilador especificada por _nnnn_ solo una vez.<br /><br /> Por ejemplo, **/wo4326** hace que la advertencia C4326 se notifique solo una vez, la primera vez que se encuentre en el compilador.

Si usa las opciones de advertencia al crear un encabezado precompilado, conserva esos valores. Al usar el encabezado precompilado, se vuelven a aplicar las mismas opciones de advertencia. Para invalidar las opciones de advertencia del encabezado precompilado, establezca otra opción de advertencia en la línea de comandos.

Puede usar una directiva de [Advertencia de #pragma](../../preprocessor/warning.md) para controlar el nivel de advertencia que se indica en tiempo de compilación en archivos de código fuente específicos.

Las directivas pragma warning del código fuente no se ven afectadas por la opción **/w** .

La [documentación de errores de compilación](../../error-messages/compiler-errors-1/c-cpp-build-errors.md) describe las advertencias y los niveles de advertencia, e indica por qué ciertas instrucciones no pueden compilarse como se pretende.

### <a name="to-set-the-compiler-options-in-the-visual-studio-development-environment"></a>Para establecer las opciones del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Para establecer las opciones **/W0**, **/W1**, **/W2**, **/W3**, **/W4**, **/Wall**, **/WV**, **/WX**o **/WX-** , seleccione **propiedades de configuración** > **C/C++**  > **General**.

   - Para establecer las opciones **/W0**, **/W1**, **/W2**, **/W3**, **/W4**o **/Wall** , modifique la propiedad **nivel de advertencia** .

   - Para establecer las opciones **/WX** o **/WX-** , modifique la propiedad **tratar advertencias como errores** .

   - Para establecer la versión de la opción **/WV** , escriba el número de versión del compilador en la propiedad **versión de advertencia** .

1. Para establecer las opciones **/WD** o **/We** , seleccione las **propiedades de configuración** > página de propiedades **avanzadas** de **C/C++**  > .

   - Para establecer la opción **/WD** , seleccione el control desplegable de la propiedad **deshabilitar advertencias específicas** y, a continuación, elija **Editar**. En el cuadro de edición del cuadro de diálogo **deshabilitar advertencias específicas** , escriba el número de advertencia. Para especificar más de una advertencia, separe los valores con un punto y coma ( **;** ). Por ejemplo, para deshabilitar C4001 y C4010, escriba **4001; 4010**. Elija **Aceptar** para guardar los cambios y volver al cuadro de diálogo **páginas de propiedades** .

   - Para establecer la opción **/We** , seleccione el control desplegable de la propiedad **tratar advertencias específicas como errores** y, a continuación, elija **Editar**. En el cuadro de edición del cuadro de diálogo **tratar advertencias específicas como errores** , escriba el número de advertencia. Para especificar más de una advertencia, separe los valores con un punto y coma ( **;** ). Por ejemplo, para tratar C4001 y C4010 como errores, escriba **4001; 4010**. Elija **Aceptar** para guardar los cambios y volver al cuadro de diálogo **páginas de propiedades** .

1. Para establecer la opción **/WO** , seleccione las **propiedades de configuración** > página de propiedades línea de **comandos** de **C/C++**  > . Escriba la opción del compilador en el cuadro **opciones adicionales** .

1. Elija **Aceptar** para guardar los cambios.

### <a name="to-set-the-compiler-option-programmatically"></a>Para establecer la opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarnAsError%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableSpecificWarnings%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

\ [Opciones del compilador MSVC](compiler-options.md)
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
