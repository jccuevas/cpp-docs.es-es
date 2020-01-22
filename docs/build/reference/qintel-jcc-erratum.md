---
title: /QIntel-jcc-erratum
description: Describe la opción/QIntel-jcc-erratum deC++ Microsoft C/Compiler (MSVC).
ms.date: 01/07/2020
f1_keywords:
- QIntel-jcc-erratum
helpviewer_keywords:
- /QIntel-jcc-erratum
- -QIntel-jcc-erratum
ms.openlocfilehash: f311da04b833b06124c5e6237ea83a31319858ca
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2020
ms.locfileid: "76520922"
---
# <a name="qintel-jcc-erratum"></a>/QIntel-jcc-erratum

::: moniker range="<=vs-2017"

La opción **/QIntel-JCC-Erratum** está disponible en la versión 16,5 de Visual Studio 2019 y versiones posteriores.

::: moniker-end

::: moniker range=">=vs-2019"

Especifica que el compilador genera instrucciones para mitigar el impacto en el rendimiento causado por la actualización de microcódigo de erratas de código condicional de Intel Jump (JCC) en determinados procesadores de Intel.

## <a name="syntax"></a>Sintaxis

> **/QIntel-jcc-erratum**

## <a name="remarks"></a>Notas

En **/QIntel-JCC-Erratum**, el compilador detecta saltos e instrucciones de saltos delimitados por macros que cruzan o finalizan en un límite de 32 bytes. Alinea estas instrucciones con el límite. Este cambio reduce el impacto en el rendimiento de las actualizaciones de microcódigo que impiden la errata JCC en determinados procesadores Intel. Para obtener más información acerca de la errata, consulte [mitigaciones para saltar la errata de código condicional](https://www.intel.com/content/dam/support/us/en/documents/processors/mitigations-jump-conditional-code-erratum.pdf) en el sitio web de Intel.

La opción **/QIntel-JCC-Erratum** está disponible en la versión 16,5 de Visual Studio 2019 y versiones posteriores. Esta opción solo está disponible en los compiladores que tienen como destino x86 y x64. La opción no está disponible en los compiladores que tienen como destino Procesadores ARM.

La opción **/QIntel-JCC-Erratum** está desactivada de forma predeterminada y solo funciona en compilaciones optimizadas. Esta opción puede aumentar el tamaño del código.

**/QIntel-JCC-Erratum** es incompatible con [/CLR](clr-common-language-runtime-compilation.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione las **propiedades de configuración** > página de propiedades **generación de código** de **C/C++**  >.

1. Seleccione un valor para la propiedad **Habilitar la mitigación de erratas de JCC de Intel** . Seleccione **Aceptar** para aplicar el cambio.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[/Q (opciones) (operaciones de bajo nivel)](q-options-low-level-operations.md)\
\ [Opciones del compilador MSVC](compiler-options.md)
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)

::: moniker-end
