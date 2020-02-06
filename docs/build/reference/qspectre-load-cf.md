---
title: /Qspectre-load-cf
description: Describe la opción deQspectre-load-cfC++ /compilador de Microsoft C/Compiler (MSVC).
ms.date: 01/28/2020
helpviewer_keywords:
- /Qspectre-load-cf
no-loc:
- Qspectre-load-cf
ms.openlocfilehash: c32b843df517cb6fbe662fba0b592cbf745f1764
ms.sourcegitcommit: 0f4ee9056d65043fa5a715f0ad1031c0ed30e2b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2020
ms.locfileid: "77035551"
---
# /Qspectre-load-cf

Especifica la generación del compilador de instrucciones de serialización para cada instrucción de flujo de control que contiene una carga. Esta opción realiza un subconjunto de las mitigaciones realizadas por la opción [/Qspectre-Load](qspectre-load.md) .

## <a name="syntax"></a>Sintaxis

> **/Qspectre-load-cf**

## <a name="remarks"></a>Observaciones

**/Qspectre-load-cf** hace que el compilador detecte `JMP`, `RET`y `CALL` instrucciones de flujo de control que se cargan desde la memoria y para insertar instrucciones de serialización después de la carga. Siempre que sea posible, estas instrucciones se dividen en una carga y una transferencia de flujo de control. La carga va seguida de un `LFENCE` para asegurarse de que la carga está protegida. Hay casos en los que el compilador no puede dividir instrucciones, como la instrucción `JMP`, por lo que utiliza una técnica de mitigación alternativa. Por ejemplo, el compilador mitiga `jmp [rax]` agregando instrucciones para cargar el destino de forma no destructiva antes de insertar un LFENCE, como se muestra aquí:

```asm
    xor rbx, [rax]
    xor rbx, [rax]  ; force a load of [rax]
    lfence          ; followed by an LFENCE
    jmp [rax]
```

Dado que **/Qspectre-load-cf** detiene la especulación de todas las cargas en las instrucciones de flujo de control, el impacto en el rendimiento es alto. La mitigación no es apropiada en todo el mundo. Si hay bloques de código críticos para el rendimiento que no requieren protección, puede deshabilitar estas mitigaciones mediante `__declspec(spectre(nomitigation))`.

La opción de **Qspectre-load-cfde/** está desactivada de forma predeterminada y admite todos los niveles de optimización.

La opción de **Qspectre-load-cfde/** está disponible en la versión 16,5 de Visual Studio 2019 y versiones posteriores. Esta opción solo está disponible en los compiladores que tienen como destino procesadores x86 y x64. No está disponible en los compiladores que tienen como destino Procesadores ARM.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

2. Seleccione las **propiedades de configuración** > página de propiedades **generación de código** de **C/C++**  > .

3. Seleccione un nuevo valor para la propiedad de **mitigación Spectre** . Seleccione **Aceptar** para aplicar el cambio.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Consulte también

[/Q (opciones) (operaciones de bajo nivel)](q-options-low-level-operations.md)\
\ [Opciones del compilador MSVC](compiler-options.md)
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
