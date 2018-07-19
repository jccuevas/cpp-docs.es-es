---
title: -Ox (habilitar la mayoría de las optimizaciones de velocidad) | Documentos de Microsoft
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
ms.openlocfilehash: 569563bff030904988e93db749438eaeb58ce9db
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378392"
---
# <a name="ox-enable-most-speed-optimizations"></a>/Ox (habilitar la mayoría de las optimizaciones de velocidad)

El **/Ox** opción del compilador permite una combinación de las optimizaciones que favorecen la velocidad. En algunas versiones del IDE de Visual Studio y el mensaje de Ayuda de compilador, esto se denomina *optimización completa*, pero la **/Ox** opción del compilador habilita solo un subconjunto de las opciones de optimización de velocidad habilitada de forma **/O2**.

## <a name="syntax"></a>Sintaxis

> /Ox

## <a name="remarks"></a>Comentarios

El **/Ox** compilador opción habilita la **/o** esa velocidad favorecer opciones del compilador. El **/Ox** opción del compilador no incluye la adición [/GF (eliminar cadenas duplicadas)](../../build/reference/gf-eliminate-duplicate-strings.md) y [/Gy (habilitar vinculación en el nivel de función)](../../build/reference/gy-enable-function-level-linking.md) opciones habilitadas por [/O1 o/O2 (minimizar tamaño, maximizar velocidad)](../../build/reference/o1-o2-minimize-size-maximize-speed.md). Las opciones adicionales que se aplica por **/O1** y **/O2** puede provocar punteros a cadenas o las funciones para compartir una dirección de destino, lo que puede afectar a la depuración y la conformidad de lenguaje estricta. El **/Ox** opción es una forma sencilla de habilitar la mayoría de las optimizaciones sin incluir **/GF** y **/Gy**. Para obtener más información, vea las descripciones de los [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) y [/Gy](../../build/reference/gy-enable-function-level-linking.md) opciones.

El **/Ox** opción del compilador es lo mismo que usar las siguientes opciones de combinación:

- [/Ob (expansión de funciones Inline)](../../build/reference/ob-inline-function-expansion.md), donde el parámetro de opción es 2 (**/Ob2**)

- [/Og (Optimizaciones globales)](../../build/reference/og-global-optimizations.md)

- [/Oi (Generar funciones intrínsecas)](../../build/reference/oi-generate-intrinsic-functions.md)

- [/Ot (favorecer código rápido)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)

- [/Oy (omisión de puntero de marco)](../../build/reference/oy-frame-pointer-omission.md)

**/Ox** es mutuamente excluyente de:

- [/ O1 (minimizar tamaño)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)

- [/ O2 (maximizar velocidad)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)

- [/Od (Deshabilitar (Depurar))](../../build/reference/od-disable-debug.md)

Puede cancelar la polarización hacia la velocidad de la **/Ox** opción del compilador si especifica **/Oxs**, que combina la **/Ox** opción del compilador con [/Os (favorecer pequeña Código)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md). Las opciones combinadas favorecen un tamaño de código.

Para aplicar todas las optimizaciones de nivel de archivo disponibles para versiones de lanzamiento, se recomienda que especifique [/O2 (maximizar velocidad)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) en lugar de **/Ox**, y [/O1 (minimizar tamaño)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) en su lugar de **/Oxs**. Para compilaciones aún más la optimización de versión, considere también la [/GL (optimización de todo el programa)](../../build/reference/gl-whole-program-optimization.md) opción del compilador y [/LTCG (generación de código de tiempo de vínculo)](../../build/reference/ltcg-link-time-code-generation.md) opción del vinculador.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. En **propiedades de configuración**, abra **C/C++** y, a continuación, elija la **optimización** página de propiedades.

1. Modificar el **optimización** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Vea también

[/O (Opciones) (Optimizar código)](../../build/reference/o-options-optimize-code.md)  
[Opciones del compilador](../../build/reference/compiler-options.md)  
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)