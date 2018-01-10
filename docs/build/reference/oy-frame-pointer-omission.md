---
title: "-Oy (omisión de puntero de marco) | Documentos de Microsoft"
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.OmitFramePointers
- /oy
dev_langs: C++
helpviewer_keywords:
- omit frame pointer
- Oy compiler option [C++]
- stack frame pointer compiler option [C++]
- -Oy compiler option [C++]
- frame pointer omission compiler option [C++]
- suppress frame pointer creation
- /Oy compiler option [C++]
ms.assetid: c451da86-5297-4c5a-92bc-561d41379853
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 15a760d1a9df383356ead2eb2d1e1b08e8b9ca57
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="oy-frame-pointer-omission"></a>/Oy (Omisión de puntero de marco)

Suprime la creación de punteros de marcos en la pila de llamadas.

## <a name="syntax"></a>Sintaxis

> /Oy [-]

## <a name="remarks"></a>Comentarios

Esta opción acelera las llamadas de función, ya que no es necesario configurar y quitar punteros de marco. También libera un registro más (EBP en Intel 386 o posterior) para almacenar variables y subexpresiones que se utilizan con frecuencia.

**/Oy** habilita la omisión de puntero de marco y **/Oy-** deshabilita la omisión. **/Oy** solo está disponible en x86 compiladores.

Si el código requiere direccionamiento basado en EBP, puede especificar el **/Oy-** opción después de la **/Ox** opción o use [optimizar](../../preprocessor/optimize.md) con el "**y**" y **desactivar** argumentos para obtener una optimización máxima con direccionamiento basado en EBP. El compilador detecta la mayoría de las situaciones en las que se requiere el direccionamiento basado en EBP (por ejemplo, con las funciones `_alloca` y `setjmp` y con el control de excepciones estructurado).

El [/Ox (habilitar más velocidad optimizaciones)](../../build/reference/ox-full-optimization.md) y [/O1, / O2 (minimizar tamaño, maximizar velocidad)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) opciones implican **/Oy**. Especificar **/Oy-** después de la **/Ox**, **/O1**, o **/O2** opción deshabilita **/Oy**, ya sea explícita o implícita.

El **/Oy** compilador opción dificulta el uso del depurador porque el compilador suprime la información de puntero de marco. Si especifica una opción del compilador de depuración ([/Z7, / Zi, /ZI](../../build/reference/z7-zi-zi-debug-information-format.md)), se recomienda que especifique el **/Oy-** opción después de cualquier otra opción de compilador de optimización.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en el **optimización** página de propiedades.

1. Modificar el **Omitir punteros de marcos** propiedad. Esta propiedad solo agrega o quita el **/Oy** opción. Si desea agregar el **/Oy-** opción, haga clic en **línea de comandos** y modificar **opciones adicionales**.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitFramePointers%2A>.

## <a name="see-also"></a>Vea también

[Opciones /O (optimizar código)](../../build/reference/o-options-optimize-code.md)

[Opciones del compilador](../../build/reference/compiler-options.md)

[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)