---
title: "-analizar (análisis de código) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.EnablePREfast
- /analyze
- VC.Project.VCCLCompilerTool.PREfastAdditionalOptions
- VC.Project.VCCLCompilerTool.PREfastAdditionalPlugins
dev_langs: C++
helpviewer_keywords:
- /analyze compiler option [C++]
- -analyze compiler option [C++]
- analyze compiler option [C++]
ms.assetid: 81da536a-e030-4bd4-be18-383927597d08
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ba76ddd10866e414d9817f628c7a1aec019964de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="analyze-code-analysis"></a>/analyze (análisis de código)
Permite utilizar análisis de código y opciones de control.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/analyze[-][:WX-][:log filename][:quiet][:stacksize number][:max_paths number][:only]  
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
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [Code Analysis for C/C ++ Overview](/visualstudio/code-quality/code-analysis-for-c-cpp-overview) y [análisis de código para advertencias de C/C ++](/visualstudio/code-quality/code-analysis-for-c-cpp-warnings).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Expanda el **propiedades de configuración** nodo.  
  
3.  Expanda el **análisis de código** nodo.  
  
4.  Seleccione la página de propiedades **General** .  
  
5.  Modifique una o varias de las **análisis de código** propiedades.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnablePREfast%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)