---
title: -analizar (análisis de código) | Documentos de Microsoft
ms.custom: ''
ms.date: 04/26/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.EnablePREfast
- /analyze
- VC.Project.VCCLCompilerTool.PREfastAdditionalOptions
- VC.Project.VCCLCompilerTool.PREfastAdditionalPlugins
dev_langs:
- C++
helpviewer_keywords:
- /analyze compiler option [C++]
- -analyze compiler option [C++]
- analyze compiler option [C++]
ms.assetid: 81da536a-e030-4bd4-be18-383927597d08
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4893f30bae3b29538c8bead637cb4d083087a57b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376590"
---
# <a name="analyze-code-analysis"></a>/analyze (análisis de código)

Permite utilizar análisis de código y opciones de control.

## <a name="syntax"></a>Sintaxis

```cmd
/analyze[-][:WX-][:log filename][:quiet][:stacksize number][:max_paths number][:only][:ruleset]
```

## <a name="arguments"></a>Argumentos

 /analyze  
 Activa el análisis en el modo predeterminado. Resultado del análisis se pasa a la **salida** ventana como otros mensajes de error. Use **/ analyze-** para desactivar explícitamente el análisis.

 /analyze:WX-  
 Especificar **/ analyze: WX -** , las advertencias de análisis de código no se trata como errores cuando se compila con **/WX**. Para más información, vea [/w, /W0, /W1, /W2, /W3, /W4, /w1, /w2, /w3, /w4, /Wall, /wd, /we, /wo, /Wv, /WX (nivel de advertencia)](../../build/reference/compiler-option-warning-level.md).

 /analyze:log `filename`  
 Los resultados detallados del analizador se escriben como XML en el archivo especificado por `filename`.

 /analyze:quiet  
 Desactiva la salida de analizador para el **salida** ventana.

 /analyze:stacksize `number`  
 El `number` parámetro que se usa con esta opción especifica el tamaño, en bytes, del marco de pila para qué advertencia [C6262](/visualstudio/code-quality/c6262) se genera. Si no se especifica este parámetro, el tamaño del marco de pila se establece de forma predeterminada en 16 KB.

 /analyze:max_paths `number`  
 El parámetro `number` que se utiliza con esta opción especifica el número máximo de rutas de acceso del código que se van a analizar. Si no se especifica este parámetro, el número se establece de forma predeterminada en 256. Si se utilizan valores más elevados, se realizará una comprobación más completa, pero el análisis podría llevar más tiempo.

 /analyze:only  
 Normalmente, el compilador genera código y realiza una mayor comprobación de la sintaxis después de ejecutar el analizador. El **/ analyze: solo** opción desactiva este paso de generación de código; Esto realiza análisis más rápido pero no se muestran errores de compilación y las advertencias que podrían detectarse en el paso de generación de código del compilador. Si el programa no contiene errores de generación de código, es posible que los resultados del análisis no sean confiables; por tanto, es recomendable que solo use esta opción si el código ha pasado previamente comprobaciones de sintaxis de generación de código sin errores.

 / analyze: conjunto de reglas `<file_path>.ruleset`  
Le permite especificar la regla que establece para analizar, incluidos los conjuntos de reglas personalizados que puede crear usted mismo. Cuando este modificador se establece, el motor de reglas es más eficaz porque excluye los miembros no de la regla especificada establecido antes de ejecutar. Cuando no se ha establecido el modificador, el motor comprueba todas las reglas.

Los conjuntos de reglas que se incluyen con Visual Studio se encuentran en **%VSINSTALLDIR%\Team Tools\Static Analysis Tools\Rule conjuntos.**

El conjunto de reglas personalizado de ejemplo siguiente indica al motor de reglas para comprobar C6001 y C26494. También puede colocar este archivo en cualquier lugar siempre que tenga un `.ruleset` extensión y proporcionar la ruta de acceso completa en el argumento.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="New Rule Set" Description=" " ToolsVersion="15.0">
  <Rules AnalyzerId="Microsoft.Analyzers.NativeCodeAnalysis" RuleNamespace="Microsoft.Rules.Native">
    <Rule Id="C6001" Action="Warning" />
    <Rule Id="C26494" Action="Warning" />
  </Rules>
</RuleSet>
```

/ analyze: complemento  
Habilita el complemento de PREfast especificado como parte del análisis de código se ejecuta. LocalEspC.dll es el complemento que implementa el análisis de código relacionados con la simultaneidad se comprueba en el intervalo de C261XX las advertencias. Por ejemplo, [C26100](/visualstudio/code-quality/c26100), [C26101](/visualstudio/code-quality/c26101),..., [C26167](/visualstudio/code-quality/c26167).

Para ejecutar LocalEspC.dll, use esta opción del compilador: **/ analyze: complemento LocalEspC.dll**

Para ejecutar CppCoreCheck.dll, primero ejecute este comando desde un símbolo del sistema para desarrolladores:

```cmd
set Esp.Extensions=CppCoreCheck.dll
```

A continuación, utilice esta opción del compilador: **/ analyze: complemento EspXEngine.dll**.

## <a name="remarks"></a>Comentarios

Para obtener más información, consulte [Code Analysis for C/C ++ Overview](/visualstudio/code-quality/code-analysis-for-c-cpp-overview) y [análisis de código para advertencias de C/C ++](/visualstudio/code-quality/code-analysis-for-c-cpp-warnings).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Expanda el **propiedades de configuración** nodo.

1. Expanda el **análisis de código** nodo.

1. Seleccione la página de propiedades **General** .

1. Modifique una o varias de las **análisis de código** propiedades.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>.

## <a name="see-also"></a>Vea también

- [Opciones del compilador](../../build/reference/compiler-options.md)
- [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)