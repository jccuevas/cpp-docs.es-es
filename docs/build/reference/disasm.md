---
title: /DISASM
ms.date: 1/17/2018
f1_keywords:
- /disasm
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
ms.openlocfilehash: 77f6f05029ec4480afb2180eab0bb57838d643a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462951"
---
# <a name="disasm"></a>/DISASM

Imprimir el desensamblado de las secciones de código en el resultado de DUMPBIN.

## <a name="syntax"></a>Sintaxis

> **/DISASM**{**:**\[**BYTES**|**NOBYTES**]}

### <a name="arguments"></a>Argumentos

**BYTES**<br/>
Incluye los bytes de instrucciones junto con los códigos de operación interpretado y los argumentos de la salida de desensamblado. Ésta es la opción predeterminada.

**NOBYTES**<br/>
No incluye los bytes de la instrucción en la salida de desensamblado.

## <a name="remarks"></a>Comentarios

El **/DISASM** opción muestra el desensamblado de las secciones de código en el archivo. Usa los símbolos de depuración si están presentes en el archivo.

**/DISASM** en imágenes nativas, no administradas, solo debe usarse. La herramienta equivalente para código administrado es [ILDASM](/dotnet/framework/tools/ildasm-exe-il-disassembler).

Solo el [/HEADERS](../../build/reference/headers.md) está disponible para su uso en los archivos generados por la opción de DUMPBIN el [/GL (optimización de todo el programa)](../../build/reference/gl-whole-program-optimization.md) opción del compilador.

## <a name="see-also"></a>Vea también

[Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)
