---
title: /DISASM
ms.date: 01/17/2018
f1_keywords:
- /disasm
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
ms.openlocfilehash: fb394b2266470e77c50ce5398aea961c37ac34fb
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927721"
---
# <a name="disasm"></a>/DISASM

Imprime el desensamblado de las secciones de código en el resultado de DUMPBIN.

## <a name="syntax"></a>Sintaxis

> **/DISASM**{ **:** \[**BYTES**|**NOBYTES**]}

### <a name="arguments"></a>Argumentos

**BYTES**<br/>
Incluye los bytes de instrucción junto con los códigos de tiempo interpretados y los argumentos en el resultado del desensamblado. Esta es la opción predeterminada.

**NOBYTES**<br/>
No incluye los bytes de instrucción en la salida del desensamblado.

## <a name="remarks"></a>Comentarios

La opción **/DISASM** muestra el desensamblado de las secciones de código en el archivo. Utiliza símbolos de depuración si están presentes en el archivo.

**/DISASM** solo se debe usar en imágenes nativas y no administradas. La herramienta equivalente para código administrado es [Ildasm](/dotnet/framework/tools/ildasm-exe-il-disassembler).

Solo la opción [/headers](headers.md) DUMPBIN está disponible para su uso en los archivos generados por la opción del compilador [/GL (optimización de todo el programa)](gl-whole-program-optimization.md) .

## <a name="see-also"></a>Vea también

[Opciones de DUMPBIN](dumpbin-options.md)
