---
title: /Qpar (Paralelizador automático)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.EnableParallelCodeGeneration
ms.assetid: 33ecf49d-c0d5-4f34-bce3-84ff03f38918
ms.openlocfilehash: c75770f834abcf17862e173e692129a43a5155c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588700"
---
# <a name="qpar-auto-parallelizer"></a>/Qpar (Paralelizador automático)

Habilita la [Paralelizador automático](../../parallel/auto-parallelization-and-auto-vectorization.md) característica del compilador automáticamente paralelizar los bucles en el código.

## <a name="syntax"></a>Sintaxis

```
/Qpar
```

## <a name="remarks"></a>Comentarios

Cuando el compilador paraleliza automáticamente bucles en el código, cálculo distribuye entre varios núcleos de procesador. Un bucle se paraleliza sólo si el compilador determina que es legal para hacerlo, y ese paralelización mejoraría el rendimiento.

El `#pragma loop()` directivas están disponibles para ayudar a que el optimizador de paralelizar los bucles específicos. Para obtener más información, consulte [bucle](../../preprocessor/loop.md).

Para obtener información acerca de cómo permitir que los mensajes de salida para el paralelizador automático, consulte [/qpar-Report (nivel de información de Paralelizador automático)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md).

### <a name="to-set-the-qpar-compiler-option-in-visual-studio"></a>Para establecer la opción del compilador /Qpar en Visual Studio

1. En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**.

1. En el **páginas de propiedades** cuadro de diálogo **C o C++**, seleccione **línea de comandos**.

1. En el **opciones adicionales** , escriba `/Qpar`.

### <a name="to-set-the-qpar-compiler-option-programmatically"></a>Para establecer la opción del compilador /Qpar mediante programación

- Use el ejemplo de código de <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[/Q (Opciones) (Operaciones de bajo nivel)](../../build/reference/q-options-low-level-operations.md)<br/>
[/Qpar/report (Nivel de información de paralelizador automático)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)<br/>
[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[#pragma loop()](../../preprocessor/loop.md)<br/>
[Programación en paralelo en código nativo](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)