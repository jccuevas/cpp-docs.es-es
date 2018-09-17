---
title: /DISASM | Microsoft Docs
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
ms.openlocfilehash: 6a5a4d930c47d2a3c2808cbd0a343c5c68de4ac9
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707192"
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
