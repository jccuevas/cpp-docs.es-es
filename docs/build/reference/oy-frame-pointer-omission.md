---
title: /Oy (Omisión de puntero de marco)
ms.date: 11/19/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.OmitFramePointers
- /oy
helpviewer_keywords:
- omit frame pointer
- Oy compiler option [C++]
- stack frame pointer compiler option [C++]
- -Oy compiler option [C++]
- frame pointer omission compiler option [C++]
- suppress frame pointer creation
- /Oy compiler option [C++]
ms.assetid: c451da86-5297-4c5a-92bc-561d41379853
ms.openlocfilehash: 7eb30a758f6888aa866620e8b419c9b4124475b0
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418124"
---
# <a name="oy-frame-pointer-omission"></a>/Oy (Omisión de puntero de marco)

Suprime la creación de punteros de marcos en la pila de llamadas.

## <a name="syntax"></a>Sintaxis

> /Oy[-]

## <a name="remarks"></a>Comentarios

Esta opción acelera las llamadas de función, ya que no es necesario configurar y quitar punteros de marco. También libera un registro de uso general.

**/Oy** permite la omisión de puntero de marco y **/Oy-** deshabilita la omisión. En x64 compiladores, **/Oy** y **/Oy-** no están disponibles.

Si el código requiere direccionamiento basado en el marco, puede especificar el **/Oy-** opción después de la **/Ox** o utilizar [optimizar](../../preprocessor/optimize.md) con el "**y**"y **desactivar** argumentos para obtener una optimización máxima con direccionamiento basado en el marco. El compilador detecta la mayoría de las situaciones donde se requiere el direccionamiento basado en fotogramas (por ejemplo, con el `_alloca` y `setjmp` funciones y con control de excepciones estructurado).

El [/Ox (habilitar más las optimizaciones de velocidad)](../../build/reference/ox-full-optimization.md) y [/O1, / O2 (minimizar tamaño, maximizar velocidad)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) opciones implican **/Oy**. Especificar **/Oy-** después de la **/Ox**, **/O1**, o **/O2** opción deshabilita **/Oy**, ya sea explícita o implícita.

El **/Oy** facilita la opción del compilador con el depurador más difícil porque el compilador suprime la información de puntero de marco. Si especifica una opción del compilador de depuración ([/Z7, / Zi, /ZI](../../build/reference/z7-zi-zi-debug-information-format.md)), se recomienda que especifique el **/Oy-** opción después de cualquier otra opción del compilador de optimización.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **optimización** página de propiedades.

1. Modificar el **Omitir punteros de marcos** propiedad. Esta propiedad solo agrega o quita el **/Oy** opción. Si desea agregar el **/Oy-** opción, seleccione el **línea de comandos** propiedad página y modificar **opciones adicionales**.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitFramePointers%2A>.

## <a name="see-also"></a>Vea también

[/O (Opciones) (Optimizar código)](../../build/reference/o-options-optimize-code.md)<br/>
[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
