---
title: /analyze (análisis de código)
ms.date: 10/01/2019
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
ms.openlocfilehash: d647045d76dc32544f8146424b220547890b0943
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816331"
---
# <a name="analyze-code-analysis"></a>/analyze (análisis de código)

Permite utilizar análisis de código y opciones de control.

## <a name="syntax"></a>Sintaxis

```cmd
/analyze[-][:WX-][:log filename][:quiet][:stacksize number][:max_paths number][:only][:ruleset]
```

## <a name="arguments"></a>Argumentos

/ANALYZE activa el análisis en el modo predeterminado. La salida del análisis va a la ventana **resultados** como otros mensajes de error. Use **/Analyze-** para desactivar explícitamente el análisis.

/ANALYZE: WX-especificando **/Analyze: WX-** significa que las advertencias de análisis de código no se tratan como errores al compilar mediante **/WX**. Para más información, vea [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (nivel de advertencia)](compiler-option-warning-level.md).

/ANALYZE: log `filename` los resultados detallados del analizador se escriben como XML en el archivo especificado por `filename`.

/ANALYZE: Quiet desactiva la salida del analizador en la ventana de **salida** .

/ANALYZE: stacksize `number` el parámetro `number` que se usa con esta opción especifica el tamaño, en bytes, del marco de pila para el que se genera la advertencia [C6262](/visualstudio/code-quality/c6262) . El espacio antes de `number` es opcional. Si no se especifica este parámetro, el tamaño del marco de pila se establece de forma predeterminada en 16 KB.

/ANALYZE: max_paths `number` el parámetro `number` que se usa con esta opción especifica el número máximo de rutas de acceso de código que se van a analizar. Si no se especifica este parámetro, el número se establece de forma predeterminada en 256. Si se utilizan valores más elevados, se realizará una comprobación más completa, pero el análisis podría llevar más tiempo.

/ANALYZE: normalmente, el compilador genera código y realiza más comprobaciones de sintaxis después de ejecutar el analizador. La opción **/Analyze: Only** desactiva este paso de generación de código; Esto hace que el análisis sea más rápido, pero no se emiten errores y advertencias de compilación que podrían haber descubierto el paso de generación de código del compilador. Si el programa no contiene errores de generación de código, es posible que los resultados del análisis no sean confiables; por tanto, es recomendable que solo use esta opción si el código ha pasado previamente comprobaciones de sintaxis de generación de código sin errores.

/ANALYZE: ruleset `<file_path>.ruleset` permite especificar los conjuntos de reglas que se van a analizar, incluidos los conjuntos de reglas personalizados que se pueden crear usted mismo. Cuando se establece este modificador, el motor de reglas es más eficaz, ya que excluye los miembros del conjunto de reglas especificado antes de ejecutarse. Cuando no se establece el modificador, el motor comprueba todas las reglas.

Los conjuntos de configuración que se incluyen con Visual Studio se encuentran en **%VSINSTALLDIR%\team Tools\Static Analysis Tools\Rule sets.**

El siguiente conjunto de reglas personalizado de ejemplo indica al motor de reglas que busque C6001 y C26494. Puede colocar este archivo en cualquier lugar siempre que tenga una extensión `.ruleset` y proporcione la ruta de acceso completa en el argumento.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

/ANALYZE: el complemento habilita el complemento de PREfast especificado como parte de las ejecuciones de análisis de código.
LocalEspC. dll es el complemento que implementa comprobaciones de análisis de código relacionadas con la simultaneidad en el intervalo de advertencias de C261XX. Por ejemplo, [C26100](/visualstudio/code-quality/c26100), [C26101](/visualstudio/code-quality/c26101),..., [C26167](/visualstudio/code-quality/c26167).

Para ejecutar LocalEspC. dll, use esta opción del compilador: **/Analyze: plugin LocalEspC. dll**

Para ejecutar CppCoreCheck. dll, primero ejecute este comando desde un símbolo del sistema para desarrolladores:

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

A continuación, use esta opción del compilador: **/Analyze: plugin EspXEngine. dll**.

## <a name="remarks"></a>Comentarios

Para obtener más información, vea [análisis de código paraC++ c/Overview](/visualstudio/code-quality/code-analysis-for-c-cpp-overview) y [análisis de códigoC++ para c/Warnings](/visualstudio/code-quality/code-analysis-for-c-cpp-warnings).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Expanda el nodo **Propiedades de configuración**.

1. Expanda el nodo **análisis de código** .

1. Seleccione la página de propiedades **General** .

1. Modifique una o varias de las propiedades de **análisis de código** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>.

## <a name="see-also"></a>Vea también

- [Opciones del compilador de MSVC](compiler-options.md)
- [Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
