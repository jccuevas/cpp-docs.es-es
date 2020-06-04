---
title: /analyze (Análisis de código)
ms.date: 10/15/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.EnablePREfast
- /analyze
- VC.Project.VCCLCompilerTool.PREfastAdditionalOptions
- VC.Project.VCCLCompilerTool.PREfastAdditionalPlugins
helpviewer_keywords:
- /analyze compiler option [C++]
- -analyze compiler option [C++]
- analyze compiler option [C++]
ms.assetid: 81da536a-e030-4bd4-be18-383927597d08
ms.openlocfilehash: c0cebe1cbd160bdec257a960f90039c1af3bfee2
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416048"
---
# <a name="analyze-code-analysis"></a>/analyze (Análisis de código)

Permite utilizar análisis de código y opciones de control.

## <a name="syntax"></a>Sintaxis

> **/Analyze**[-] [ **: WX-** ] [ **: log** *nombreDeArchivo*] [ **: Quiet**] [ **: stacksize** *número*] [ **: max_paths** *número*] [ **: Only**] [ **: ruleset** *ruleset*] [ **:p** *archivo. dll de complemento de*Lugin]

## <a name="arguments"></a>Argumentos

\ de **/Analyze**
Activa el análisis en el modo predeterminado. La salida del análisis va a la ventana **resultados** como otros mensajes de error. Use **/Analyze-** para desactivar explícitamente el análisis.

**/Analyze: WX-** \
Las advertencias de análisis de código no se tratan como errores al compilar mediante **/WX**. Para obtener más información, vea [/WX (nivel de advertencia)](compiler-option-warning-level.md).

**/Analyze: log** *filename*\
Los resultados detallados del analizador se escriben como XML en el archivo especificado por *filename*.

**/Analyze:\ silencioso**
Desactiva el resultado del analizador en la ventana de **salida** .

**/Analyze: stacksize** *número*\
El parámetro *Number* que se usa con esta opción especifica el tamaño, en bytes, del marco de pila para el que se genera la advertencia [C6262](/cpp/code-quality/c6262) . El espacio antes del *número* es opcional. Si no se especifica este parámetro, el tamaño del marco de pila es de 16 KB de forma predeterminada.

**/Analyze: max_paths** *número*\
El parámetro *Number* que se usa con esta opción especifica el número máximo de rutas de acceso de código que se van a analizar. Si no se especifica este parámetro, el número es 256 de forma predeterminada. Los valores mayores causan una comprobación más exhaustiva, pero el análisis puede tardar más tiempo.

**/Analyze: solo**\
Normalmente, el compilador genera código y realiza una mayor comprobación de la sintaxis después de ejecutar el analizador. La opción **/Analyze: Only** desactiva este paso de generación de código. Agiliza el análisis, pero los errores y advertencias de compilación que el paso de generación de código del compilador podría encontrar no se emiten. Si el programa no está libre de errores de generación de código, es posible que los resultados del análisis no sean confiables. Se recomienda usar esta opción solo si el código ya pasa la comprobación de sintaxis de generación de código sin errores.

**/Analyze: ruleset** *file_path. ruleset*\
Permite especificar los conjuntos de reglas que se van a analizar, incluidos los conjuntos de reglas personalizados que se pueden crear usted mismo. Cuando se establece este modificador, el motor de reglas es más eficaz, ya que excluye los miembros del conjunto de reglas especificado antes de ejecutarse. De lo contrario, el motor comprueba todas las reglas.

Los conjuntos de configuración que se incluyen con Visual Studio se encuentran en *%VSINSTALLDIR%\team Tools\Static Analysis Tools\Rule sets.*

El siguiente conjunto de reglas personalizado de ejemplo indica al motor de reglas que busque C6001 y C26494. Puede colocar este archivo en cualquier lugar, siempre que tenga una extensión de `.ruleset` y proporcione la ruta de acceso completa en el argumento.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

**/Analyze:** complemento *de complemento-dll*\
Habilita el complemento de PREfast especificado como parte de las ejecuciones de análisis de código.

::: moniker range="<=vs-2017"

LocalEspC. dll es el complemento que implementa comprobaciones de análisis de código relacionadas con la simultaneidad en el intervalo de advertencias de C261XX. Por ejemplo, [C26100](/cpp/code-quality/c26100), [C26101](/cpp/code-quality/c26101),..., [C26167](/cpp/code-quality/c26167).

Para ejecutar LocalEspC. dll, use esta opción del compilador: **/Analyze: plugin LocalEspC. dll**

::: moniker-end
::: moniker range=">=vs-2019"

ConcurrencyCheck. dll implementa comprobaciones de análisis de código relacionadas con la simultaneidad en el intervalo de advertencias de C261XX. Por ejemplo, [C26100](/cpp/code-quality/c26100), [C26101](/cpp/code-quality/c26101),..., [C26167](/cpp/code-quality/c26167).

Para ejecutar ConcurrencyCheck. dll, primero ejecute este comando desde un símbolo del sistema para desarrolladores:

```cmd
set Esp.Extensions=ConcurrencyCheck.dll
```

A continuación, use esta opción del compilador: **/Analyze: plugin EspXEngine. dll**.

::: moniker-end

Para ejecutar CppCoreCheck. dll, primero ejecute este comando desde un símbolo del sistema para desarrolladores:

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

A continuación, use esta opción del compilador: **/Analyze: plugin EspXEngine. dll**.

## <a name="remarks"></a>Observaciones

Para obtener más información, vea [análisis de código paraC++ c/Overview](/cpp/code-quality/code-analysis-for-c-cpp-overview) y [análisis de códigoC++ para c/Warnings](/cpp/code-quality/code-analysis-for-c-cpp-warnings).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione las **propiedades de configuración** > página de propiedades **General** > **análisis de código** .

1. Modifique una o varias de las propiedades de **análisis de código** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>.

## <a name="see-also"></a>Consulte también

\ [Opciones del compilador MSVC](compiler-options.md)
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
