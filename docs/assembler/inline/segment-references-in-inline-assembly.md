---
title: Referencias de segmento de ensamblado insertado
ms.date: 08/30/2018
helpviewer_keywords:
- references, inline assembly
- segment references in inline assembly
- inline assembly, segment references
- registers
- inline assembly, registers
- registers, inline assembly
ms.assetid: c63e6bb4-49d9-4fa1-bb22-eea21b5cbc0f
ms.openlocfilehash: 5c07fa897da23a55f376a20e7588c8c8c269d1a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577338"
---
# <a name="segment-references-in-inline-assembly"></a>Referencias de segmento de ensamblado insertado

**Específicos de Microsoft**

Debe hacer referencia a los segmentos por registro en lugar de por nombre (el nombre de segmento `_TEXT` no es válido, por ejemplo). Los reemplazos de segmento deben usar el registro explícitamente, como en ES:[BX].

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>