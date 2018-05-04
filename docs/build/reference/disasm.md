---
title: / DISASM | Documentos de Microsoft
ms.date: 1/17/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /disasm
dev_langs:
- C++
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 89b0784ff10e7d9521351e01d8907c963c9304fd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="disasm"></a>/DISASM

Imprimir el desensamblado de las secciones de código en el resultado de DUMPBIN.

## <a name="syntax"></a>Sintaxis

> **/ DISASM**{**:**\[**BYTES**|**NOBYTES**]}  

### <a name="arguments"></a>Argumentos

**BYTES**  
Incluye los bytes de instrucción junto con los códigos de operación interpretados y los argumentos en la salida de desensamblado. Ésta es la opción predeterminada.

**NOBYTES**  
No incluye los bytes de la instrucción en la salida de desensamblado.

## <a name="remarks"></a>Comentarios

El **/DISASM** opción muestra el desensamblado de las secciones de código en el archivo. Utiliza símbolos de depuración, si están presentes en el archivo.

**/ DISASM** solo debe usarse en las imágenes nativas, no administradas,. La herramienta equivalente para código administrado es [ILDASM](/dotnet/framework/tools/ildasm-exe-il-disassembler).

Solo el [/HEADERS](../../build/reference/headers.md) opción de DUMPBIN está disponible para su uso en archivos generados por el [/GL (optimización de todo el programa)](../../build/reference/gl-whole-program-optimization.md) opción del compilador.

## <a name="see-also"></a>Vea también

[Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)  
