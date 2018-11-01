---
title: /Qvec-report (Nivel de información de vectorizador automático)
ms.date: 11/04/2016
ms.assetid: 4778c9a3-0692-4085-9b05-1bfeadf4c74a
ms.openlocfilehash: dc8c1d3bc65b0160fd489f1cdebe06e4fc9a0992
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590234"
---
# <a name="qvec-report-auto-vectorizer-reporting-level"></a>/Qvec-report (Nivel de información de vectorizador automático)

Habilita la característica informes del compilador [Vectorizador automático](../../parallel/auto-parallelization-and-auto-vectorization.md) y especifica el nivel de los mensajes informativos de salida durante la compilación.

## <a name="syntax"></a>Sintaxis

```
/Qvec-report:{1}{2}
```

## <a name="remarks"></a>Comentarios

**/ Qvec-report: 1**<br/>
Genera un mensaje informativo para los bucles que se ha vectorizado.

**/ Qvec-report: 2**<br/>
Genera un mensaje informativo para los bucles que se ha vectorizado y para los bucles que no vectorizados, junto con un código de motivo.

Para obtener información sobre los códigos de motivo y mensajes, vea [mensajes del Vectorizador y Paralelizador](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

### <a name="to-set-the-qvec-report-compiler-option-in-visual-studio"></a>Para establecer la opción del compilador /Qvec-report en Visual Studio

1. En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**.

1. En el **páginas de propiedades** cuadro de diálogo **C o C++**, seleccione **línea de comandos**.

1. En el **opciones adicionales** , escriba `/Qvec-report:1` o `/Qvec-report:2`.

### <a name="to-set-the-qvec-report-compiler-option-programmatically"></a>Para establecer la opción del compilador /Qvec-report mediante programación

- Use el ejemplo de código de <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[/Q (Opciones) (Operaciones de bajo nivel)](../../build/reference/q-options-low-level-operations.md)<br/>
[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[Programación en paralelo en código nativo](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)