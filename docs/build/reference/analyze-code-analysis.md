---
title: /analyze (análisis de código)
ms.date: 04/26/2018
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
ms.openlocfilehash: 057fabe9612f84af07649d7a4f7bbf6d83e01f6c
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426217"
---
# <a name="analyze-code-analysis"></a>/analyze (análisis de código)

Permite utilizar análisis de código y opciones de control.

## <a name="syntax"></a>Sintaxis

```cmd
/analyze[-][:WX-][:log filename][:quiet][:stacksize number][:max_paths number][:only][:ruleset]
```

## <a name="arguments"></a>Argumentos

/ analyze activa en el análisis en el modo predeterminado. Salida de análisis se dirige a la **salida** ventana como otros mensajes de error. Use **/ analyze:** para desactivar explícitamente el análisis.

/ analyze: WX-especificar **/ analyze: WX -** significa que las advertencias de análisis de código no se trata como errores cuando se compila utilizando **/WX**. Para más información, vea [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (nivel de advertencia)](../../build/reference/compiler-option-warning-level.md).

/ analyze: log `filename` resultados detallados del analizador se escriben como XML en el archivo especificado por `filename`.

/ analyze: quiet vueltas desactivar los resultados del analizador en la **salida** ventana.

/ analyze: stacksize `number` el `number` parámetro que se usa con esta opción especifica el tamaño, en bytes, del marco de pila para qué advertencia [C6262](/visualstudio/code-quality/c6262) se genera. Si no se especifica este parámetro, el tamaño del marco de pila se establece de forma predeterminada en 16 KB.

/ analyze: max_paths `number` el `number` parámetro que se usa con esta opción especifica el número máximo de rutas de acceso del código que se va a analizar. Si no se especifica este parámetro, el número se establece de forma predeterminada en 256. Si se utilizan valores más elevados, se realizará una comprobación más completa, pero el análisis podría llevar más tiempo.

/ analyze: solo por lo general, en que el compilador genera código y hace más de comprobación después de ejecutar el analizador de sintaxis. El **/ analyze: solo** opción desactiva esta fase de generación de código; Esto hace que análisis más rápido, pero no se emiten advertencias que podrían haber sido detectadas por la fase de generación de código del compilador y errores de compilación. Si el programa no contiene errores de generación de código, es posible que los resultados del análisis no sean confiables; por tanto, es recomendable que solo use esta opción si el código ha pasado previamente comprobaciones de sintaxis de generación de código sin errores.

/ analyze: ruleset `<file_path>.ruleset` le permite especificar qué regla se establece para analizar, incluidos los conjuntos de reglas personalizados que puede crear usted mismo. Cuando este modificador se establece, el motor de reglas es más eficaz porque excluye a los miembros de la regla especificada establecido antes de ejecutar. Cuando el modificador no se establece, el motor comprueba todas las reglas.

Los conjuntos de reglas que se suministran con Visual Studio se encuentran en **%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule conjuntos.**

El conjunto de reglas personalizado de ejemplo siguiente indica al motor de reglas para comprobar C6001 y C26494. Puede colocar este archivo en cualquier lugar, siempre tiene un `.ruleset` extensión y proporcionar la ruta de acceso completa en el argumento.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

/ analyze: plugin permite que el complemento de PREfast especificado como parte del análisis de código se ejecuta.
LocalEspC.dll es el complemento que implementa el análisis de código relacionados con la simultaneidad comprueba las advertencias de intervalo de C261XX. Por ejemplo, [C26100](/visualstudio/code-quality/c26100), [C26101](/visualstudio/code-quality/c26101),..., [C26167](/visualstudio/code-quality/c26167).

Para ejecutar LocalEspC.dll, use esta opción del compilador: **/ analyze: plugin LocalEspC.dll**

Para ejecutar CppCoreCheck.dll, primero ejecute este comando desde un símbolo del sistema para desarrolladores:

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

A continuación, utilice esta opción del compilador: **/ analyze: plugin EspXEngine.dll**.

## <a name="remarks"></a>Comentarios

Para obtener más información, consulte [análisis de código para C/C ++ Overview](/visualstudio/code-quality/code-analysis-for-c-cpp-overview) y [análisis de código para advertencias de C/C ++](/visualstudio/code-quality/code-analysis-for-c-cpp-warnings).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Expanda el nodo **Propiedades de configuración**.

1. Expanda el **análisis de código** nodo.

1. Seleccione la página de propiedades **General** .

1. Modificar uno o varios de los **análisis de código** propiedades.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>.

## <a name="see-also"></a>Vea también

- [Opciones del compilador](../../build/reference/compiler-options.md)
- [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)
