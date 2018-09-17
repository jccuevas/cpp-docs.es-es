---
title: -Ox (habilitar la mayoría de las optimizaciones de velocidad) | Microsoft Docs
ms.custom: ''
ms.date: 09/25/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.ToolOptimization
- /ox
dev_langs:
- C++
helpviewer_keywords:
- Ox compiler option [C++]
- fast code [C++]
- /Ox compiler option [C++]
- -Ox compiler option [C++]
ms.assetid: 3ad7c30b-c615-428c-b1d0-2e024f81c760
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d93bfe44fab0400ce4c3c173473601745f85196c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721531"
---
# <a name="ox-enable-most-speed-optimizations"></a>/Ox (habilitar la mayoría de las optimizaciones de velocidad)

El **/Ox** opción del compilador permite una combinación de optimizaciones que favorecer la velocidad. En algunas versiones del IDE de Visual Studio y el mensaje de Ayuda de compilador, esto se denomina *optimización completa*, pero la **/Ox** habilita la opción del compilador solo un subconjunto de las opciones de optimización de velocidad habilitada de forma **/O2**.

## <a name="syntax"></a>Sintaxis

> /Ox

## <a name="remarks"></a>Comentarios

El **/Ox** habilita la opción del compilador la **/O** opciones del compilador de esa favorecer la velocidad. El **/Ox** opción del compilador no incluye el adicionales [/GF (eliminar cadenas duplicadas)](../../build/reference/gf-eliminate-duplicate-strings.md) y [/Gy (habilitar vinculación en el nivel de función)](../../build/reference/gy-enable-function-level-linking.md) opciones habilitadas por [/O1 o/O2 (minimizar tamaño, maximizar velocidad)](../../build/reference/o1-o2-minimize-size-maximize-speed.md). Las opciones adicionales que se aplican por **/O1** y **/O2** puede hacer que los punteros a cadenas o a las funciones para compartir una dirección de destino, lo que puede afectar a la depuración y la conformidad estricta del lenguaje. El **/Ox** opción es una manera fácil de habilitar la mayoría de las optimizaciones sin incluir **/GF** y **/Gy**. Para obtener más información, consulte las descripciones de los [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) y [/Gy](../../build/reference/gy-enable-function-level-linking.md) opciones.

El **/Ox** opción del compilador es lo mismo que usar las siguientes opciones de combinación:

- [/Ob (expansión de funciones insertadas)](../../build/reference/ob-inline-function-expansion.md), donde el parámetro de opción es 2 (**/Ob2**)

- [/Og (Optimizaciones globales)](../../build/reference/og-global-optimizations.md)

- [/Oi (Generar funciones intrínsecas)](../../build/reference/oi-generate-intrinsic-functions.md)

- [/Ot (favorecer código rápido)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)

- [/Oy (omisión de puntero de marco)](../../build/reference/oy-frame-pointer-omission.md)

**/Ox** es mutuamente excluyente de:

- [/ O1 (minimizar tamaño)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)

- [/ O2 (maximizar velocidad)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)

- [/Od (Deshabilitar (Depurar))](../../build/reference/od-disable-debug.md)

Puede cancelar la inclinación hacia la velocidad de la **/Ox** opción del compilador si especifica **/Oxs**, que combina el **/Ox** con la opción del compilador [/Os (favorecer pequeño Código)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md). Las opciones combinadas favorecen el tamaño más pequeño de código.

Para aplicar todas las optimizaciones de nivel de archivo disponibles para las compilaciones de versión, se recomienda que especifique [/O2 (maximizar velocidad)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) en lugar de **/Ox**, y [/O1 (minimizar tamaño)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) en su lugar de **/Oxs**. Para compilaciones de optimización aún más en la versión, considere también la [/GL (Whole Program Optimization)](../../build/reference/gl-whole-program-optimization.md) opción del compilador y [/LTCG (generación de código de tiempo de vínculo)](../../build/reference/ltcg-link-time-code-generation.md) opción del vinculador.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. En **propiedades de configuración**, abra **C o C++** y, a continuación, elija el **optimización** página de propiedades.

1. Modificar el **optimización** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Vea también

[Opciones /O (optimizar código)](../../build/reference/o-options-optimize-code.md)
[opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)