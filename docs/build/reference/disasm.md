---
title: /DISASM
ms.date: 1/17/2018
f1_keywords:
- /disasm
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
ms.openlocfilehash: 10e8187e896b3922438a8cf2dafa0aec4c91f904
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272066"
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

Solo el [/HEADERS](headers.md) está disponible para su uso en los archivos generados por la opción de DUMPBIN el [/GL (optimización de todo el programa)](gl-whole-program-optimization.md) opción del compilador.

## <a name="see-also"></a>Vea también

[Opciones de DUMPBIN](dumpbin-options.md)
