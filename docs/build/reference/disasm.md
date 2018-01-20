---
title: /DISASM | Microsoft Docs
ms.date: 1/17/2018
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /disasm
dev_langs: C++
helpviewer_keywords:
- -DISASM dumpbin option
- DISASM dumpbin option
- /DISASM dumpbin option
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d448b92c3436f3d2875bd8d9b8e0af6a7149e065
ms.sourcegitcommit: ff9bf140b6874bc08718674c07312ecb5f996463
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/19/2018
---
# <a name="disasm"></a>/DISASM

Imprimir el desensamblado de las secciones de código en el resultado de DUMPBIN.

## <a name="syntax"></a>Sintaxis

> **/DISASM**{**:**\[**BYTES**|**NOBYTES**]}  

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
