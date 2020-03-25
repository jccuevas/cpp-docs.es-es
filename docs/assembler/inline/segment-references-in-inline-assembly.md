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
ms.openlocfilehash: 865fc5fac5f46cdc8c55966e9989227d1d671d6f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169258"
---
# <a name="segment-references-in-inline-assembly"></a>Referencias de segmento de ensamblado insertado

**Específicos de Microsoft**

Debe hacer referencia a los segmentos por registro en lugar de por nombre (el nombre de segmento `_TEXT` no es válido, por ejemplo). Los reemplazos de segmento deben usar el registro explícitamente, como en ES:[BX].

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Uso del lenguaje de ensamblado en bloques __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
