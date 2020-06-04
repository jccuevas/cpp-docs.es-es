---
title: /Qpar-report (Nivel de información de paralelizador automático)
ms.date: 11/04/2016
ms.assetid: 562673b9-02da-4bf8-bb64-70bc25ef4651
ms.openlocfilehash: 25732900fa201258331dcb8eee96af9ba97a6def
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319959"
---
# <a name="qpar-report-auto-parallelizer-reporting-level"></a>/Qpar-report (Nivel de información de paralelizador automático)

Habilita la característica informes del compilador [Paralelizador automático](../../parallel/auto-parallelization-and-auto-vectorization.md) y especifica el nivel de los mensajes informativos de salida durante la compilación.

## <a name="syntax"></a>Sintaxis

```
/Qpar-report:{1}{2}
```

## <a name="remarks"></a>Comentarios

**/Qpar-report:1**<br/>
Genera un mensaje informativo para los bucles que se paralelizan.

**/Qpar-report:2**<br/>
Genera un mensaje informativo para los bucles que se paralelizan y también para los bucles que no se paralelizan, junto con un código de motivo.

Los mensajes se notifican a stdout. Si no se notifica ningún mensaje informativo, significa que el código no contiene bucles, o bien que el nivel de generación de informes no se estableció para notificar bucles no paralelizados. Para obtener más información sobre los códigos de motivo y mensajes, vea [mensajes del Vectorizador y Paralelizador](../../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).

### <a name="to-set-the-qpar-report-compiler-option-in-visual-studio"></a>Cómo establecer la opción del compilador /Qpar-report en Visual Studio

1. En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**.

1. En el **páginas de propiedades** cuadro de diálogo **C o C++**, seleccione **línea de comandos**.

1. En el **opciones adicionales** , escriba `/Qpar-report:1` o `/Qpar-report:2`.

### <a name="to-set-the-qpar-report-compiler-option-programmatically"></a>Cómo establecer la opción del compilador /Qpar-report mediante programación

- Use el ejemplo de código de <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[/Q (Opciones) (Operaciones de bajo nivel)](q-options-low-level-operations.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[Programación en paralelo en código nativo](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/04/12/auto-vectorizer-in-visual-studio-2012-overview/)
