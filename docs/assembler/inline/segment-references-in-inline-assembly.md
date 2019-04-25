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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167379"
---
# <a name="segment-references-in-inline-assembly"></a>Referencias de segmento de ensamblado insertado

**Específicos de Microsoft**

Debe hacer referencia a los segmentos por registro en lugar de por nombre (el nombre de segmento `_TEXT` no es válido, por ejemplo). Los reemplazos de segmento deben usar el registro explícitamente, como en ES:[BX].

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>